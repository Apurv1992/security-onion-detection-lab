# Security Onion Detection Engineering Lab

## Overview

This repository documents my personal Detection Engineering and Threat Hunting lab built using Security Onion.

The lab is used to simulate adversary techniques using Atomic Red Team, collect telemetry through Sysmon and Elastic Agent, and develop detections mapped to the MITRE ATT&CK framework.

## Lab Environment

* Security Onion 2.4
* Windows Server 2022 (Active Directory Domain Controller)
* Windows 11 Enterprise
* Sysmon
* Elastic Agent
* Atomic Red Team

## Objectives

* Detection Engineering
* Threat Hunting
* Sigma Rule Development
* MITRE ATT&CK Mapping
* Security Analytics

## Current Detections

| Technique                    | ATT&CK ID | Status     |
| ---------------------------- | --------- | ---------- |
| System Information Discovery | T1082     | ✅ Complete |
| PowerShell                   | T1059.001 | ✅ Complete |
| Account Discovery            | T1033     | ✅ Complete |
| Brute Force                  | T1110     | ✅ Complete |
| Valid Accounts               | T1078     | ✅ Complete |

## Repository Structure

```text
security-onion-detection-lab/
│
├── README.md
├── lab-setup/
│
└── detections/
    ├── T1082-System-Information-Discovery/
    ├── T1059.001-PowerShell/
    ├── T1033-Account-Discovery/
    ├── T1110-Brute-Force/
    └── T1078-Valid-Accounts/
```

## Planned Detections

* T1053.005 Scheduled Task Creation
* T1547 Registry Run Keys / Startup Folder
* T1003 Credential Dumping
* T1105 Ingress Tool Transfer
* T1562 Impair Defenses

## Disclaimer

This repository is intended for educational and research purposes only. All testing and attack simulations were performed in an isolated lab environment.

