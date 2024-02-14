---
layout: page
title: Active TLS Stack Fingerprinting Data
permalink: /data/atsf/
description: "This pages describes the data published for the TMA Paper \"Active TLS Stack Fingerprinting: Characterizing TLS Server Deployments at Scale\"."
---

Our data are published at [TUM University Library](https://mediatum.ub.tum.de/1658435) to enable reproducible analyses and to guarantee long-term availability.<br>
Dataset: [DOI:10.14459/2022mp1658435](https://doi.org/10.14459/2022mp1658435)



The data set contains the raw measurement data from the section *Longitudinal Study of Toplists and Blocklists*.
The dataset consists of 25 measurements and the following files for each measurement:

* scan (TLS and HTTP data obtained with the goscanner)
    * certs.csv (deduplicated certificates observed in the measurements)
    * cert_chain.csv (certificate signature chains constructed for each handshake)
    * hosts.csv.input (input list labels for each handshake)
    * hosts.csv (main tls scan results)
    * http.csv (collected http data)
    * http_verbose (all observed HTTP headers and their order)
    * tls_verbose.csv (extended TLS data used for fingerprinting)
    * tls_fingerprints.csv (derived fingerprints for each [IP address, port, servername] target)
* client-hellos (all client hellos used in the measurement)
* abuse_ch_sslbl (blocked certificate hashes dowloaded in the measurement week from the [SSLBL](https://sslbl.abuse.ch/))
* Mapping used to identify the AS for each IP observed in this measurement

Our measurements are based on multiple input lists and we have labeled each TLS handshake with the source where we have found the the domain or IP address.
Possible sources:

* Alexa Top 1 Million
* [Majestic Million](https://majestic.com/reports/majestic-million/)
* [Feodo](https://feodotracker.abuse.ch/)
* [SSLBL](https://sslbl.abuse.ch/)
                                                                                
The `tls_fingerprints.csv` contains multiple fingerprints as columns. Columns ending with `_sr` contain the fingerprint including the Status Request extension:
While the scan also contains other Clien Hellos we only used the [10 general-purpose Client Hellos](https://github.com/active-tls-fingerprinting/client-hellos) from the paper for fingerprinting.
* fingerprint_random is collected with the 10 random CHs                        
* fingerprint_jarm is collected with the 10 JARM CHs                            
* fingerprint_all with all CHs
* The separate fingerprint obtained with each CH  
