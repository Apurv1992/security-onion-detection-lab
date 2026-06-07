# Security Onion Detection Engineering Lab

## Overview

This repository documents my personal Detection Engineering and Threat Hunting lab built using Security Onion.

The lab is used to simulate adversary techniques using Atomic Red Team, collect telemetry through Sysmon and Elastic Agent, and develop detections mapped to the MITRE ATT&CK framework.

## Lab Environment

- Security Onion 2.4
- Windows Server 2022 (Active Directory)
- Windows Endpoint
- Sysmon
- Elastic Agent
- Atomic Red Team

## Objectives

- Detection Engineering
- Threat Hunting
- Sigma Rule Development
- MITRE ATT&CK Mapping
- Security Analytics

## Current Detections

| Technique | ATT&CK ID | Status |
|------------|------------|---------|
| System Information Discovery | T1082 | Complete |

## Planned Detections

- T1059.001 PowerShell
- T1110 Password Spraying
- T1078 Valid Accounts
- T1003 Credential Dumping
- T1021 Remote Services
