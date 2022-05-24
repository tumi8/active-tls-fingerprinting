---
layout: page
title: Measurement Pipeline
permalink: /pipeline/
---

Our measurement and fingerprinting pipeline is separated into the following steps:
- Domain resolution
- Input preparation
- TLS scanning
- Post processing

### Domain resolution

Every domain from the input sets needs to be resolved first. For this have used a local [unbound](https://www.nlnetlabs.nl/projects/unbound/about/) server and [massdns](https://github.com/blechschmidt/massdns). The following command can generate the appropriate input file for the TLS scanner.

{% highlight bash %}
bin/massdns -r local_resolvers.txt input_domains.txt -q -o J \
  | jq '[.name,.data.answers[-1].data]  | @csv' -r \
  | csvtool col 1,2 - | awk -F, '$2!=""' > input.csv
{% endhighlight %}

This input file is then joined with the IP address inputs we collect from the blocklists (because the lists do not contain any domain names we could resolve).

### Input preparation

To scan the targets we additionally need to provide the Client Hello for scanning. The final input for the scanner is a cross-product between the input from the last section and a set of client hello names. We use the goscanner to calculate this cross-product. Shall the directory `client-hellos` contain the Client Hellos for the scan. This could be e.g., the general-purpose Client Hellos desined for the paper - downloadable [here](https://github.com/active-tls-fingerprinting/client-hellos).

{% highlight bash %}
goscanner create-ch-input --ch-dir ./client-hellos --input input.csv | shuf > input-final.csv
{% endhighlight %}

We shuffle the input to distribute the load among the scanned servers.

### TLS scanning

To scan the targets we configure the TLS scanner with the following configuration:

{% highlight conf %}
; Input file with IP,domain,client hello tuples
input-file = "input-full.csv"

; Output directory (must not exist as scanner will refuse to override existing output)
output = "tls-scanner-output"

; Limit the requests per second to reduce load on targets
qps = 500

; Store the HTTP Header (not necessary for fingerprinting)
http-headers = "Server"

; Enable extended TLS output to collect the fingerprintable information
tls-extended-output = true

; Provide the Client Hello Directory
client-hello-dir = "client-hellos"

; use the TLS and HTTP function of the scanner
scans = "tls"
scans = "http"
{% endhighlight %}

### Post processing

The raw output of the scanner does not contain the final fingerprints of the servers, because they are a combination of the results from multiple requests.
To generate the fingerints for each target we added this functionality to the goscanner.

{% highlight bash %}
goscanner generate-fingerprints --scanner-dir ./tls-scanner-output -ch-dir ./client-hellos
{% endhighlight %}