# Lab Architecture

## Overview

This lab was built to support Detection Engineering, Threat Hunting, Sigma Rule Development, and Security Analytics using Security Onion.

The environment simulates a small enterprise Active Directory network and generates realistic telemetry for detection development and adversary emulation.

---

## Architecture Diagram

```text
                    +----------------------+
                    |      SO01            |
                    |  Security Onion      |
                    |      2.4.210         |
                    +----------+-----------+
                               |
                               |
                    -----------------------
                               |
          -------------------------------------------
          |                                         |
          |                                         |
+---------+---------+                 +-------------+-------------+
|   DC01.lab.local  |                 |      WIN11-01            |
| Windows Server    |                 | Windows 11 Endpoint      |
| Active Directory  |                 | Sysmon + Elastic Agent   |
| DNS               |                 | Atomic Red Team          |
+-------------------+                 +--------------------------+
```

---

## Components

### SO01 - Security Onion

Role:

* SIEM
* Log Management
* Threat Hunting
* Alerting
* Detection Validation

Version:

* Security Onion 2.4.210

Telemetry Sources:

* Sysmon
* Windows Security Logs
* Active Directory Events

---

### DC01.lab.local

Operating System:

* Windows Server 2022

Services:

* Active Directory Domain Services (AD DS)
* DNS

Telemetry:

* Authentication Events
* Kerberos Events
* Group Membership Changes
* Account Management Activity

---

### WIN11-01

Operating System:

* Windows 11

Installed Components:

* Sysmon
* Elastic Agent
* Atomic Red Team

Purpose:

* Attack Simulation
* Detection Validation
* Threat Hunting Exercises

---

## Telemetry Flow

```text
WIN11-01
   |
   | Sysmon Events
   | Windows Security Logs
   |
Elastic Agent
   |
   v
Security Onion

DC01
   |
   | Authentication Events
   | Kerberos Events
   |
Elastic Agent
   |
   v
Security Onion
```

---

## Detection Engineering Workflow

1. Execute ATT&CK Technique
2. Generate Telemetry
3. Analyze Events in Security Onion
4. Develop Detection Logic
5. Create Sigma Rule
6. Validate Detection
7. Document Findings
8. Publish Detection Content

---

## Current Focus Areas

* MITRE ATT&CK Mapping
* Sigma Rule Development
* Threat Hunting
* Sysmon Analysis
* Security Onion Detection Engineering
* Atomic Red Team Simulations
