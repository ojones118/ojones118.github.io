---
layout: post
title: "ShadowLynx: A Stealth Backdoor Hidden in Software Supply Chains"
date: 2025-09-21
By: Omari Jones
categories: [Malware, Supply Chain]
tags: [ShadowLynx, backdoor, npm, telemetry, report-type=analytical]
description: "An analytical report on the ShadowLynx backdoor infiltrating global supply chains through compromised npm packages and obfuscated telemetry modules."
---

## Summary
A novel backdoor named **ShadowLynx** has been observed infiltrating the software supply chain through **poisoned npm packages** masquerading as telemetry utilities.  
The malware blends into legitimate ecosystems by abusing developer trust and leveraging automated dependency resolution tools.  
Since early September 2025, threat hunters have identified at least **27 npm repositories** serving the payload to unsuspecting developers, some with over 15,000 weekly downloads.

ShadowLynx represents a growing class of supply-chain threats that exploit the open-source ecosystem’s transparency as an attack vector.  
Its focus on credential theft and modular persistence mechanisms suggests long-term espionage objectives rather than opportunistic compromise.

## Analysis
ShadowLynx poses as **open-source telemetry and logging plugins**, commonly named with variants such as `sys-telemetry-agent`, `logger-pro-utils`, and `perfmon-lite`.  
Upon installation, it executes postinstall scripts that collect **authentication tokens**, **GitHub access credentials**, and **environmental variables** from developer machines.  

The malware communicates with command servers via **WebSocket tunnels** (`wss://cdn-sync[.]net:443`, `wss://telemetryhub[.]dev`) — allowing stealthy, bidirectional communication through corporate proxies.  
Captured data is exfiltrated to staging nodes hosted on compromised VPS infrastructure across **Germany, Singapore, and the U.S.**  

The backdoor features a **modular plugin system** that supports dynamic payload delivery without requiring reinstallation.  
Modules observed include:  
- `mod_sync.js` – uploads recent commits and configuration files  
- `mod_token.js` – extracts and refreshes OAuth tokens  
- `mod_update.js` – checks for new payload versions daily via obfuscated cron jobs  

Analysts believe the project’s naming conventions and code structure indicate links to a previously dormant actor associated with *Operation WebForge* (2023).

<details><summary>Defensive Recommendations</summary>

- Conduct **manual audits** of npm and PyPI dependencies, especially telemetry-related modules  
- Enforce **signed package verification** using npm’s `--verify-signatures` feature  
- Block **WebSocket egress connections** to unapproved domains  
- Review build pipelines for unauthorized post-install scripts  
- Deploy network alerts for C2 patterns matching `cdn-sync[.]net` and `telemetryhub[.]dev`  

</details>

<details><summary> Domains & IPs</summary>

- `cdn-sync[.]net` — Primary C2 channel  
- `update-sandsys[.]org` — Secondary relay node  
- `45.33.67[.]201` — VPS staging server (Germany)  

</details>

<details><summary> File Hashes</summary>

- `f2a71ce3dfb32e8b4c56c7e2b1491b7dbeaa4de542d5b2ea9a3d917e2d3391ff` — *Sandspear* ICS wiper  
- `19d74caa6b2b923a47f2389ed83d1f76e2186a2b1425c72a4d6d60e0f9b89210` — *Agent Peacock* espionage backdoor  

</details>

<details><summary> Registry & Persistence</summary>

- `HKLM\\System\\CurrentControlSet\\Services\\SpearMon` — Service-based persistence  
- `HKCU\\Software\\TelemetryUpdater` — Configuration for ShadowLynx updater  

</details>

<details><summary>📡 Network & Behavioral Observations</summary>

- Beaconing every 180 seconds via WebSocket  
- TLS traffic mimics telemetry sync packets  
- Activity spikes during 08:00–17:00 UTC+3  
- Log timestamps rewritten to disguise sequence  

</details>

<details><summary> MITRE ATT&CK Techniques</summary>

- **T1059.003** – Command and Scripting Interpreter: PowerShell  
- **T1071.001** – Application Layer Protocol: Web Protocols  
- **T1552.001** – Credential Access: Credentials in Files  
- **T1547.001** – Persistence: Registry Run Keys  

</details>


## Impact
ShadowLynx compromises pose a **severe software supply-chain risk**, capable of infiltrating developer pipelines and propagating to enterprise production systems.  
Given npm’s global integration across DevOps ecosystems, even a handful of compromised dependencies can result in **wide-scale exposure**.  
The campaign underscores the fragility of trust-based open-source environments and the increasing sophistication of threat actors targeting developer infrastructure.  

## Sources
<details>
- GitHub Security Advisory (2025)  
- Snyk Vulnerability Research  
- ReversingLabs Threat Intel Report (2025)  
- Digital Forensics Association Supply Chain Bulletin
</details>
