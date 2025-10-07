---
layout: post
title: "Healthcare Sector Hit by Ransomware-as-a-Service"
date: 2025-10-10
By: Omari Jones
categories: [Malware, Ransomware, Healthcare]
tags: [ind=healthcare, type=ransomware, RaaS, mal=LockBit, report-type=analytical]
description: "Analytical report on recent healthcare ransomware incidents using RaaS operations."
---
## Summary
A coordinated campaign leveraging Ransomware-as-a-Service (RaaS) platforms has struck several hospitals aOperators behind the LockBit and MedusaLocker variants exploited VPN flaws and phishing emails.
## Analysis
Post-exploitation disables security tools, exfiltrates EHR data, and encrypts local storage.
Ransom demands range from 2 – 10 BTC with data-leak threats.
Incident responders noted similar ransom portals across all victims, implying a single affiliate.
<details><summary>Detection and Containment Tips</summary>
- Monitor for suspicious PowerShell executions from service accounts
- Maintain immutable backups
- Patch VPN appliances and enforce MFA
</details>
## Impact
Operational disruption and financial strain on smaller clinics.
## Sources
- HHS HC3 Alert 2025-14
- Mandiant Healthcare Threat Report
