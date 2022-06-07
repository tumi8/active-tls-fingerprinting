---
layout: home
---

Additional material of the publication *Active TLS Stack Fingerprinting: 
Characterizing TLS Server Deployments at Scale* and access to published
data and tools.

## Measurement Pipeline and Software

For the analyses of the paper we have developed [10 general-purpose Client Hellos](https://github.com/active-tls-fingerprinting/client-hellos) and extended the [Goscanner](https://github.com/tumi8/goscanner) with a [custom TLS library](https://github.com/tumi8/goscanner/tree/master/tls) and TLS fingerprinting functionalities:

- Export of fingerprintable TLS metadata
- Ability to define arbitrary Client Hellos per target
- A random Client Hello generator
- Input list preparation

Active TLS fingerprinting with the goscanner is desigend to be used in a more comprehensive measurement pipeline.
The steps to reproduce the fingerprinting used in the paper are described under [Pipeline](/pipeline/).
If you use the goscanner for fingerprinting, please cite our paper.

## Paper

**Abstract** 
Active measurements can be used to collect server characteristics on a large scale. This kind of metadata can help discovering hidden relations and commonalities among server deployments offering new possibilities to cluster and classify them. As an example, identifying a previously-unknown cybercriminal infrastructures can be a valuable source for cyber-threat intelligence. We propose herein an active measurement-based methodology for acquiring Transport Layer Security (TLS) metadata from servers and leverage it for their fingerprinting. Our fingerprints capture the characteristic behavior of the TLS stack primarily caused by the implementation, configuration, and hardware support of the underlying server. Using an empirical optimization strategy that maximizes information gain from every handshake to minimize measurement costs, we generated 10 general-purpose Client Hellos used as scanning probes to create a large database of TLS configurations used for classifying servers. We fingerprinted 28 million servers from the Alexa and Majestic toplists and two Command and Control (C2) blocklists over a period of 30 weeks with weekly snapshots as foundation for two long-term case studies: classification of Content Delivery Network and C2 servers. The proposed methodology shows a precision of more than 99 % and enables a stable identification of new servers over time. This study describes a new opportunity for active measurements to provide valuable insights into the Internet that can be used in security-relevant use cases.

**Paper** Read the final version of our paper at the **[[TMA]](https://tma.ifip.org/2022/)**

**Authors** [Markus Sosnowski](https://net.in.tum.de/~sosnowski), [Johannes Zirngibl](https://net.in.tum.de/~zirngibl), [Patrick Sattler](https://net.in.tum.de/~sattler), [Georg Carle](https://net.in.tum.de/~carle), Claas Grohnfeldt, Michele Russo, and Daniele Sgandurra

## Reproducibility

Our data are published at [TUM University Library](https://mediatum.ub.tum.de/1658435) to enable reproducible analyses and to guarantee long-term availability.<br>
Dataset DOI: [10.14459/2022mp1658435](https://doi.org/10.14459/2022mp1658435)

Details of the data are described [here](/data/).

