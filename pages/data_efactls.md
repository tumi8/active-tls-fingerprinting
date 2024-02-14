---
layout: page
title: EFACTLS Data
permalink: /data/efactls/
description: "This pages describes the data published for the TNSM Paper \"EFACTLS: Effective Active TLS Fingerprinting for Large-scale Server Deployment Characterization\"."
---

Our data are published at [TUM University Library](https://mediatum.ub.tum.de/1733820) to enable reproducible analyses and to guarantee long-term availability.<br>
Dataset: [DOI:10.14459/2024mp1733820](https://doi.org/10.14459/2024mp1733820)


The data set contains the raw measurement data from the section *Longitudinal Study of Toplists and Blocklists*.
The dataset consists of weekly measurements and the top, blocklist, and pyasn data used for the analyses.
We stored our measruement data as [parquet files](https://parquet.apache.org/).
We recommend reading them with pandas or pyspark.


The folder structure is as follows:
* ssl (main TLS and HTTP data obtained with the goscanner used for fingerprinting)
  * all_parsed (the scan data)
    * certs (deduplicated certificates observed in the measurements)
    * cert_chain (certificate signature chains constructed for each handshake)
    * hosts.input (input list labels for each handshake)
    * hosts (main tls scan results)
    * http (collected http data)
    * http_verbose (all observed HTTP headers and their order)
    * tls_verbose (extended TLS data used for fingerprinting)
  * client-hellos (all client hellos used in the measurement)
* ssl-systematic (JARM and DissecTLS data used to compare the approaches)
  * all_parsed (the scan data, similar as above)
    * jarm (the results obtained with the JARM module of the Goscanner)
    * dissectls (the DissecTLS results)
* blocklists (the used blocklists downloaded daily)
* pyasn (the Pyasn files used to identify the AS for each IP observed in this measurement, downloaded daily. We always used the file downloaded on the same date as the TLS measurements for the mapping)
* tranco (The Tranco toplist used as input)

