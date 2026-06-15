# Security Onion Detection Engineering Lab

## Overview

This repository documents my personal Detection Engineering and Threat Hunting lab built using Security Onion.

The lab is used to simulate adversary techniques, collect telemetry through Sysmon and Elastic Agent, and develop detections mapped to the MITRE ATT&CK framework.

Each detection includes attack simulation, threat hunting, Sigma rule development, and validation using telemetry generated within the lab environment.

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
* Security Onion Operations

## Current Detections

| ATT&CK ID | Technique                    | Status     |
| --------- | ---------------------------- | ---------- |
| T1082     | System Information Discovery | ✅ Complete |
| T1059.001 | PowerShell                   | ✅ Complete |
| T1033     | Account Discovery            | ✅ Complete |
| T1110     | Brute Force                  | ✅ Complete |
| T1078     | Valid Accounts               | ✅ Complete |
| T1053.005 | Scheduled Task Creation      | ✅ Complete |

## Repository Structure

```text
security-onion-detection-lab/
│
├── README.md
├── detections/
│   ├── README.md
│   ├── T1033/
│   ├── T1053.005/
│   ├── T1059.001/
│   ├── T1078/
│   ├── T1082/
│   └── T1110/
│
└── lab-setup/
```

## Planned Detections

* T1547 – Registry Run Keys / Startup Folder
* T1003 – Credential Dumping
* T1105 – Ingress Tool Transfer
* T1562 – Impair Defenses
* T1055 – Process Injection
* T1218 – Signed Binary Proxy Execution

## Skills Demonstrated

* Detection Engineering
* Threat Hunting
* Security Onion
* Sigma Rule Development
* Windows Event Analysis
* Sysmon Telemetry Analysis
* Active Directory Security Monitoring
* MITRE ATT&CK Mapping
* Security Operations (SOC)

## Disclaimer

This repository is intended for educational and research purposes only. All testing and attack simulations were performed in an isolated lab environment.

