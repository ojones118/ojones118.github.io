---
layout: post
title: "APT-44 Expands Espionage Operations in South Asia"
date: 2025-06-07
By: Omari Jones
categories: [APT, Espionage]
tags: [APT44, type=espionage, geo=south-Asia, report-type=analytical]
description: "Technical assessment of APT-44 espionage campaigns targeting South Asian ministries."
---
<p align="center">
  <img src="/assets/apt44.png" alt="apt44" width="700">
</p>
## Summary
APT-44, believed to be state-linked, expanded espionage across South Asian energy and defense ministries.
## Analysis
Phishing lures deliver Excel documents that install a loader named “FalconDrop.”
It deploys a PowerShell backdoor with persistent task-based execution.
Data exfiltration occurs via HTTPS to compromised NGO domains.
<details><summary>TTPs Observed</summary>
- T1566.001 – Spearphishing Attachment
- T1059.001 – PowerShell
- T1041 – Exfiltration over C2 Channel
</details>
## Impact
Long-term compromise of sensitive diplomatic communications.
## Sources
- Mandiant Geo-Political Threat Bulletin (Oct 2025)
- Recorded Future Intel Brief
