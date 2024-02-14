---
layout: page
toc: Home
order: 1
description: "Additional material of the publications \"EFACTLS: Effective Active TLS Fingerprinting for Large-scale Server Deployment Characterization\" and \"Active TLS Stack Fingerprinting: Characterizing TLS Server Deployments at Scale\". We provide access to published data and tools."
---


The original paper was published at the [TMA 2022](https://tma.ifip.org/2022/) and received the **Best Paper Award**.
An **Extended Version** was published at [IEEE TNSM](https://www.comsoc.org/publications/journals/ieee-tnsm) based on new data and a new time frame.

**Authors:**
{% for author in site.data.authors.list %}<a style="border-bottom: none" href="https://orcid.org/{{author.orcid}}">
<img src="assets/ORCIDiD_icon16x16.png" style="width: 1em; margin-inline-start: 0.5em;" alt="ORCID iD icon"/></a>
[{{author.name}}](https://orcid.org/{{author.orcid}}){% if author.name contains "Sgan" %}{% else %}, {% endif %}
{% endfor %}

### Measurement Pipeline and Software

For the analyses of the paper we have developed [10 general-purpose Client Hellos](https://github.com/tumi8/active-tls-fingerprinting) and extended the [Goscanner](https://github.com/tumi8/goscanner) with a [custom TLS library](https://github.com/tumi8/goscanner/tree/master/tls) and TLS fingerprinting functionalities:

- Export of fingerprintable TLS metadata
- Ability to define arbitrary Client Hellos per target
- A random Client Hello generator
- Input list preparation

Active TLS fingerprinting with the goscanner is desigend to be used in a more comprehensive measurement pipeline.
The steps to reproduce the fingerprinting used in the paper are described under [Pipeline]({{site.baseurl}}{% link pages/pipeline.md %}).
If you use the goscanner for fingerprinting, please cite our paper.

### EFACTLS: Effective Active TLS Fingerprinting for Large-scale Server Deployment Characterization

Extended Version of our Active TLS Fingerprinting work. Access the paper under [DOI:10.1109/TNSM.2024.3364526](https://doi.org/10.1109/TNSM.2024.3364526).
Details of the data are described [here]({{site.baseurl}}{% link pages/data_efactls.md %}).

<div class="accordion-box">
  <div class="accordion-box__title">
    Abstract
  </div>
  <div class="accordion-box__content">
      <p>Active measurements allow the collection of server characteristics on a large scale that can aid in discovering hidden relations and commonalities among server deployments. Finding these relations opens up new possibilities for clustering and classifying server deployments; for example, identifying a previously unknown cybercriminal infrastructure can be valuable cyber-threat intelligence. In this work, we propose a methodology based on active measurements to acquire Transport Layer Security (TLS) metadata from servers and leverage it for fingerprinting. Our fingerprints capture characteristic behavior of the TLS stack, primarily influenced by the server’s implementation, configuration, and hardware support. Using an empirical optimization strategy that maximizes information gained from every handshake to minimize measurement costs, we generated 10 general-purpose Client Hellos. They served as scanning probes to create an extensive database of TLS configurations to classify servers. We propose the Shannon Entropy to measure collected information and compare different approaches. This study fingerprinted 8 million servers from the Tranco top list and two Command and Control (C2) blocklists over 60 weeks with weekly snapshots. The resulting data formed the foundation for two long-term case studies: classification of Content Delivery Network and C2 servers. Moreover, the detection was fine-grained enough to detect C2 server families. The proposed methodology demonstrated a precision of 99% and enabled a stable identification of new servers over time. This study shows how active measurements can provide valuable security-relevant insights and improve our understanding of the Internet.</p>
  </div>
</div><br>

If you are referring to our work or use the collected data in your publication, you can use the following:

```bib
{% raw %}@article{sosnowski2024efactls,
  author = {Sosnowski, Markus and Zirngibl, Johannes and Sattler, Patrick and Carle, Georg and Grohnfeldt, Claas and Russo, Michele and Sgandurra, Daniele},
  journal = {{IEEE Transactions on Network and Service Management}},
  title = {{EFACTLS: Effective Active TLS Fingerprinting for Large-scale Server Deployment Characterization}},
  keywords = {Servers;Fingerprint recognition;Protocols;Behavioral sciences;Probes;Internet;Feature extraction;Active Scanning;TLS;Fingerprinting;Server Classification;Command and Control Servers},
  year = {2024},
  month = feb,
  doi = {10.1109/TNSM.2024.3364526},
}{% endraw %}
```

### Active TLS Stack Fingerprinting: Characterizing TLS Server Deployments at Scale

Original TMA paper, read the final version published over ifip: **[[PDF]](https://dl.ifip.org/db/conf/tma/tma2022/tma2022-paper35.pdf)**. 
Details of the data are described [here]({{site.baseurl}}{% link pages/data_atsf.md %}).

<div class="accordion-box">
  <div class="accordion-box__title">
    Abstract
  </div>
  <div class="accordion-box__content">
      <p>Active measurements can be used to collect server characteristics on a large scale. This kind of metadata can help discovering hidden relations and commonalities among server deployments offering new possibilities to cluster and classify them. As an example, identifying a previously-unknown cybercriminal infrastructures can be a valuable source for cyber-threat intelligence. We propose herein an active measurement-based methodology for acquiring Transport Layer Security (TLS) metadata from servers and leverage it for their fingerprinting. Our fingerprints capture the characteristic behavior of the TLS stack primarily caused by the implementation, configuration, and hardware support of the underlying server. Using an empirical optimization strategy that maximizes information gain from every handshake to minimize measurement costs, we generated 10 general-purpose Client Hellos used as scanning probes to create a large database of TLS configurations used for classifying servers. We fingerprinted 28 million servers from the Alexa and Majestic toplists and two Command and Control (C2) blocklists over a period of 30 weeks with weekly snapshots as foundation for two long-term case studies: classification of Content Delivery Network and C2 servers. The proposed methodology shows a precision of more than 99 % and enables a stable identification of new servers over time. This study describes a new opportunity for active measurements to provide valuable insights into the Internet that can be used in security-relevant use cases.</p>
  </div>
</div><br>


If you are referring to our work or use the collected data in your publication, you can use the following:

```bib
{% raw %}@inproceedings{sosnowski2022tlsfingerprinting,
  author = {Sosnowski, Markus and Zirngibl, Johannes and Sattler, Patrick and Carle, Georg and Grohnfeldt, Claas and Russo, Michele and Sgandurra, Daniele},
  title = {{Active TLS Stack Fingerprinting: Characterizing TLS Server Deployments at Scale}},
  booktitle = {Proc. Network Traffic Measurement and Analysis Conference (TMA)},
  year = {2022},
  month = jun,
}{% endraw %}
```


