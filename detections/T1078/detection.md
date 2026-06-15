# T1078 - Valid Accounts

## Summary

Valid Accounts (T1078) is a common technique used by adversaries to gain or maintain access to systems using legitimate credentials. Because authentication is performed using valid accounts, this activity can be difficult to distinguish from normal user behavior.

For this detection, I generated successful domain logons within my Active Directory lab environment and analyzed the resulting Windows Security Event logs in Security Onion. The objective was to establish visibility into successful account usage and identify authentication activity that may warrant further investigation when combined with additional context.

## Attack Simulation

To generate authentication events, I successfully authenticated to the Windows endpoint using a domain user account.

The activity generated Windows Security Event ID 4624 (Successful Logon) events which were forwarded to Security Onion for analysis.

The following authentication methods were tested:

* Interactive Logon
* Network Logon
* RunAs Authentication

## Detection

The detection monitors Windows Security Event ID 4624 and focuses on commonly observed user authentication types:

* Logon Type 2 (Interactive)
* Logon Type 3 (Network)
* Logon Type 10 (Remote Interactive / RDP)

To reduce noise, common Windows system accounts were excluded, including:

* SYSTEM
* LOCAL SERVICE
* NETWORK SERVICE
* UMFD-*
* DWM-*

The detection provides visibility into successful user authentication events and can be used as a building block for higher fidelity detections involving unusual account activity.

## Validation Results

The successful authentication attempts generated Windows Security Event ID 4624 events and were successfully ingested into Security Onion.

The Sigma rule correctly identified user logon activity while filtering common Windows service and system accounts.

The resulting events provided visibility into:

* User Account
* Source Workstation
* Source IP Address
* Logon Type
* Authentication Timeline

## Hunt Query

```kql
event.code:4624
```

Additional filtering can be applied to focus on specific users, hosts, or logon types during investigations.

## Evidence

The following screenshots were captured during testing and validation:

1. Successful domain authentication from the Windows endpoint.
2. Windows Security Event ID 4624 observed in Security Onion.
3. Hunt results displaying successful logon activity.
4. Detection alert generated from the authentication event.

Screenshots are available in the `screenshots/` directory for this detection.

## Key Takeaways

Successful logons are common in enterprise environments and are not inherently suspicious. However, monitoring valid account usage is essential because many adversaries rely on legitimate credentials to blend into normal activity.

This detection provides a foundation for identifying suspicious authentication patterns such as unusual login locations, privileged account usage, lateral movement, and successful logons following multiple failed authentication attempts.

## References

* MITRE ATT&CK T1078 – Valid Accounts
* Windows Security Event ID 4624 – Successful Logon
* Security Onion

