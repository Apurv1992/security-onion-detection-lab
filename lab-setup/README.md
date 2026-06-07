# Security Onion Detection Engineering Lab

## Overview

This repository documents my personal Detection Engineering and Threat Hunting lab built using Security Onion, Active Directory, Sysmon, and Atomic Red Team.

The objective of this lab is to simulate adversary techniques, collect telemetry, develop detections, validate Sigma rules, and perform threat hunting activities mapped to the MITRE ATT&CK framework.

---

## Lab Architecture

```text
                    +----------------------+
                    |   Security Onion     |
                    |      2.4.210         |
                    | SIEM / NIDS / SOAR   |
                    +----------+-----------+
                               |
                    -----------------------
                               |
          -------------------------------------------
          |                                         |
          |                                         |
+---------+---------+                 +-------------+-------------+
|   DC01.lab.local  |                 |      WIN11-01            |
| Windows Server    |                 | Windows 11 Endpoint      |
| AD DS + DNS       |                 | Sysmon + Elastic Agent   |
+-------------------+                 +--------------------------+
```

---

## Technology Stack

### Security Monitoring

* Security Onion 2.4.210
* Elastic Stack
* Fleet / Elastic Agent
* Sysmon

### Infrastructure

* Windows Server 2022
* Active Directory Domain Services (AD DS)
* DNS
* Windows 11 Endpoint

### Detection Engineering

* Sigma Rules
* MITRE ATT&CK Mapping
* Security Onion Detections
* KQL Hunting Queries

### Adversary Simulation

* Atomic Red Team
* Manual Attack Emulation

---

## Objectives

* Build practical Detection Engineering skills
* Develop and validate Sigma rules
* Perform MITRE ATT&CK mapped threat simulations
* Conduct threat hunting investigations
* Improve Security Onion detection capabilities
* Document detection logic and lessons learned

---

## Current Detection Coverage

| Technique                    | ATT&CK ID | Status      |
| ---------------------------- | --------- | ----------- |
| System Information Discovery | T1082     | In Progress |

---

## Planned Detection Projects

### Discovery

* T1082 – System Information Discovery
* T1033 – Account Discovery

### Execution

* T1059.001 – PowerShell

### Credential Access

* T1110 – Brute Force
* T1003 – Credential Dumping

### Lateral Movement

* T1021 – Remote Services

### Persistence

* T1547 – Registry Run Keys

---

## Repository Structure

```text
security-onion-detection-lab/

├── lab-setup/
├── detections/
├── hunts/
├── sigma-rules/
└── screenshots/
```

---

## Author

Apurv Deoghare, CISSP

Cybersecurity professional with 11+ years of experience in SIEM engineering, security operations, threat detection, and security platform support.

Current areas of focus:

* Detection Engineering
* Threat Hunting
* Security Analytics
* SIEM Engineering
* MITRE ATT&CK
