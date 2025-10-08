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

<details><summary>📊 IOC Table</summary>

| **Type** | **Indicator** | **Description** |
|-----------|----------------|-------------------------|
| File Hash | `f2a71ce3dfb32e8b4c56c7e2b1491b7dbeaa4de542d5b2ea9a3d917e2d3391ff` | Sandspear wiper binary |
| File Hash | `19d74caa6b2b923a47f2389ed83d1f76e2186a2b1425c72a4d6d60e0f9b89210` | ShadowLynx payload module |
| Domain | `cdn-sync[.]net` | Primary C2 channel |
| Domain | `telemetryhub[.]dev` | Secondary C2 server |
| IP | `45.33.67[.]201` | VPS staging node |
| Registry | `HKLM\\System\\CurrentControlSet\\Services\\SpearMon` | Creates persistence service |
| File | `agent_peacock.dll` | Espionage backdoor |
| Behavior | Beacon every 180s | WebSocket exfiltration |
| MITRE TTP | T1059, T1071.001 | Scripting & Web Protocols |

</details>


## Impact
ShadowLynx compromises pose a **severe software supply-chain risk**, capable of infiltrating developer pipelines and propagating to enterprise production systems.  
Given npm’s global integration across DevOps ecosystems, even a handful of compromised dependencies can result in **wide-scale exposure**.  
The campaign underscores the fragility of trust-based open-source environments and the increasing sophistication of threat actors targeting developer infrastructure.  

## Sources
- GitHub Security Advisory (2025)  
- Snyk Vulnerability Research  
- ReversingLabs Threat Intel Report (2025)  
- Digital Forensics Association Supply Chain Bulletin
