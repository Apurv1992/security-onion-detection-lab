# Security Onion Detection Engineering Lab

## Overview

This repository documents my personal Detection Engineering and Threat Hunting lab built using Security Onion.

The lab is used to simulate adversary techniques with Atomic Red Team, collect telemetry through Sysmon and Elastic Agent, and develop detections mapped to the MITRE ATT&CK framework.

Each detection includes:

* Attack simulation
* Threat hunting queries
* Sigma detection rules
* Security Onion validation
* ATT&CK mapping
* Supporting screenshots

---

## Lab Environment

### Infrastructure

* Security Onion 2.4
* Windows Server 2022 (Active Directory)
* Windows Endpoint

### Telemetry Sources

* Sysmon
* Elastic Agent
* Windows Event Logs

### Attack Simulation

* Atomic Red Team

---

## Objectives

* Detection Engineering
* Threat Hunting
* Sigma Rule Development
* MITRE ATT&CK Mapping
* Security Analytics
* Security Onion Content Development

---

## Detection Coverage

| ATT&CK ID | Technique                          | Tactic                       | Status |
| --------- | ---------------------------------- | ---------------------------- | ------ |
| T1033     | Account Discovery                  | Discovery                    | ✅      |
| T1053.005 | Scheduled Task Creation            | Persistence                  | ✅      |
| T1059.001 | PowerShell                         | Execution                    | ✅      |
| T1078     | Valid Accounts                     | Initial Access / Persistence | ✅      |
| T1082     | System Information Discovery       | Discovery                    | ✅      |
| T1105     | Ingress Tool Transfer              | Command and Control          | ✅      |
| T1110     | Brute Force                        | Credential Access            | ✅      |
| T1218.010 | Regsvr32                           | Defense Evasion / Execution  | ✅      |
| T1218.011 | Rundll32                           | Defense Evasion / Execution  | ✅      |
| T1547.001 | Registry Run Keys / Startup Folder | Persistence                  | ✅      |
| T1562.001 | Impair Defenses                    | Defense Evasion              | ✅      |

---

## Detection Statistics

* Total Detections: 11
* Sigma Rules Developed: 11
* Detection Playbooks: 11
* Security Onion Validated: Yes
* Atomic Red Team Validated: Yes

---

## Skills Demonstrated

### Detection Engineering

* Sigma Rule Development
* Detection Validation
* ATT&CK-Based Detection Mapping
* Alert Tuning and Testing

### Threat Hunting

* Security Onion Hunt Queries
* Process Creation Analysis
* Registry Activity Analysis
* Authentication Event Analysis

### Security Monitoring

* Sysmon Telemetry Analysis
* Windows Event Log Analysis
* Security Event Investigation
* SIEM Detection Development

### Adversary Emulation

* Atomic Red Team
* ATT&CK Technique Simulation
* Detection Validation Testing

### Security Platforms

* Security Onion
* Elastic Agent
* Sysmon
* Active Directory

---

## Repository Structure

```text
detections/
├── T1033
├── T1053.005
├── T1059.001
├── T1078
├── T1082
├── T1105
├── T1110
├── T1218.010
├── T1218.011
├── T1547.001
└── T1562.001
```

---

## Detection Methodology

Each detection follows a consistent workflow:

1. Simulate the ATT&CK technique using Atomic Red Team or manual execution.
2. Collect telemetry through Sysmon and Windows Event Logs.
3. Analyze events within Security Onion.
4. Develop and validate Sigma detection rules.
5. Create hunt queries for threat hunting activities.
6. Document findings and supporting evidence.

---

## Next Phase

### Linux & Network Detection Engineering

Planned detections:

* T1021.004 – SSH
* T1046 – Network Service Discovery
* T1018 – Remote System Discovery
* T1059.004 – Bash

Future lab expansion:

* Ubuntu Server
* Kali Linux
* Zeek Network Telemetry
* Linux Detection Engineering

---

## Author

**Apurv Deoghare**

Security Engineer | Detection Engineering | Threat Hunting | SIEM Engineering

