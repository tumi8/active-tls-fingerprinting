---
layout: page
toc: Home
order: 1
---

Additional material of the publication *Active TLS Stack Fingerprinting: 
Characterizing TLS Server Deployments at Scale* and access to published
data and tools.

The paper was published at the [TMA 2022](https://tma.ifip.org/2022/) and received the **Best Paper Award**.

An **Extended Version** is planned, based on new data and a new time frame. We will publish our measurement results here. **(TBD)**.

## Measurement Pipeline and Software

For the analyses of the paper we have developed [10 general-purpose Client Hellos](https://github.com/tumi8/active-tls-fingerprinting) and extended the [Goscanner](https://github.com/tumi8/goscanner) with a [custom TLS library](https://github.com/tumi8/goscanner/tree/master/tls) and TLS fingerprinting functionalities:

- Export of fingerprintable TLS metadata
- Ability to define arbitrary Client Hellos per target
- A random Client Hello generator
- Input list preparation

Active TLS fingerprinting with the goscanner is desigend to be used in a more comprehensive measurement pipeline.
The steps to reproduce the fingerprinting used in the paper are described under [Pipeline]({{site.baseurl}}{% link pages/pipeline.md %}).
If you use the goscanner for fingerprinting, please cite our paper.

## Paper

**Abstract** 
Active measurements can be used to collect server characteristics on a large scale. This kind of metadata can help discovering hidden relations and commonalities among server deployments offering new possibilities to cluster and classify them. As an example, identifying a previously-unknown cybercriminal infrastructures can be a valuable source for cyber-threat intelligence. We propose herein an active measurement-based methodology for acquiring Transport Layer Security (TLS) metadata from servers and leverage it for their fingerprinting. Our fingerprints capture the characteristic behavior of the TLS stack primarily caused by the implementation, configuration, and hardware support of the underlying server. Using an empirical optimization strategy that maximizes information gain from every handshake to minimize measurement costs, we generated 10 general-purpose Client Hellos used as scanning probes to create a large database of TLS configurations used for classifying servers. We fingerprinted 28 million servers from the Alexa and Majestic toplists and two Command and Control (C2) blocklists over a period of 30 weeks with weekly snapshots as foundation for two long-term case studies: classification of Content Delivery Network and C2 servers. The proposed methodology shows a precision of more than 99 % and enables a stable identification of new servers over time. This study describes a new opportunity for active measurements to provide valuable insights into the Internet that can be used in security-relevant use cases.

**Paper** Read the final version of our paper published over ifip: **[[PDF]](https://tma.ifip.org/2022/wp-content/uploads/sites/11/2022/06/tma2022-paper35.pdf)**

**Authors**
{% for author in site.data.authors.list %}<a style="border-bottom: none" href="https://orcid.org/{{author.orcid}}">
<img src="assets/ORCIDiD_icon16x16.png" style="width: 1em; margin-inline-start: 0.5em;" alt="ORCID iD icon"/></a>
[{{author.name}}](https://orcid.org/{{author.orcid}}){% if author.name contains "Sgan" %}{% else %}, {% endif %}
{% endfor %}

## Referencing our Work

If you are referring to our work or use the collected data in your publication, please refer to it with the following reference [[bib]]({{ site.baseurl }}{% link assets/sosnowski2022tlsfingerprinting.bib %}):

```bib
{% raw %}@inproceedings{sosnowski2022tlsfingerprinting,
  author = {Sosnowski, Markus and Zirngibl, Johannes and Sattler, Patrick and Carle, Georg and Grohnfeldt, Claas and Russo, Michele and Sgandurra, Daniele},
  title = {{Active TLS Stack Fingerprinting: Characterizing TLS Server Deployments at Scale}},
  booktitle = {Proc. Network Traffic Measurement and Analysis Conference (TMA)},
  year = {2022},
  month = jun,
}{% endraw %}
```


## Reproducibility

Our data are published at [TUM University Library](https://mediatum.ub.tum.de/1658435) to enable reproducible analyses and to guarantee long-term availability.<br>
Dataset DOI: [10.14459/2022mp1658435](https://doi.org/10.14459/2022mp1658435)

Details of the data are described [here]({{site.baseurl}}{% link pages/data.md %}).

