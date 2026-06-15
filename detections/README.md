# Detection Catalog

This directory contains ATT&CK-mapped detections developed and validated within the Security Onion Detection Engineering Lab.

Each detection includes:

* Attack Simulation
* Detection Logic
* Sigma Rule
* Threat Hunting Queries
* Validation Results
* Supporting Evidence

## Detection Coverage

| ATT&CK ID | Technique                    | Description                                                                                                |
| --------- | ---------------------------- | ---------------------------------------------------------------------------------------------------------- |
| T1082     | System Information Discovery | Detects execution of system information discovery commands such as `systeminfo`, `hostname`, and `whoami`. |
| T1059.001 | PowerShell                   | Detects PowerShell execution commonly associated with attacker activity.                                   |
| T1033     | Account Discovery            | Detects commands used to identify the current user context.                                                |
| T1110     | Brute Force                  | Detects excessive failed authentication attempts against user accounts.                                    |
| T1078     | Valid Accounts               | Monitors successful authentication activity using valid credentials.                                       |
| T1053.005 | Scheduled Task Creation      | Detects creation of scheduled tasks using `schtasks.exe`.                                                  |

## ATT&CK Coverage

### Discovery

* T1082 – System Information Discovery
* T1033 – Account Discovery

### Execution

* T1059.001 – PowerShell

### Credential Access

* T1110 – Brute Force

### Persistence

* T1078 – Valid Accounts
* T1053.005 – Scheduled Task Creation

## Planned Detections

* T1547 – Registry Run Keys / Startup Folder
* T1003 – Credential Dumping
* T1105 – Ingress Tool Transfer
* T1562 – Impair Defenses
* T1055 – Process Injection
* T1218 – Signed Binary Proxy Execution

## Notes

All detections were developed and tested in a controlled lab environment using Security Onion, Windows Active Directory, Sysmon, and Atomic Red Team.

