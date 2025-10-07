---
layout: post
title: "Financial Sector Sees Surge in Infostealer Campaigns"
date: 2025-05-11
By: Omari Jones
categories: [Malware, Finance]
tags: [ind=finance, type=infostealer, RedLine, report-type=analytical]
description: "Analytical coverage of RedLine and Vidar campaigns targeting financial institutions."
---
## Summary
Infostealer malware campaigns are rising against financial institutions worldwide.
## Analysis
RedLine and Vidar target browser-stored credentials and crypto wallets.
Infection via malvertising and tax lure emails.
Exfiltration occurs to C2 servers using HTTPS with hard-coded domains.
<details><summary>Detection Notes</summary>
- Monitor for encoded PowerShell downloads
- Network indicators: 185.225.xxx.xxx
- Artifacts in %AppData%\Roaming\Wallets
</details>
## Impact
Credential theft and unauthorized transactions in financial systems.
## Sources
- Group-IB Threat Update (2025)
- CISA Alert AA25-101A
