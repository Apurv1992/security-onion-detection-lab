# T1562.001 - Impair Defenses

## Summary

Impair Defenses is a defense evasion technique in which adversaries modify or disable security controls to avoid detection and increase the likelihood of successful compromise.

For this detection, Microsoft Defender real-time monitoring was disabled on a Windows endpoint. The resulting registry modification event was collected by Sysmon, analyzed in Security Onion, and used to develop a Sigma detection rule.

## Attack Simulation

A PowerShell command was executed to disable Microsoft Defender real-time monitoring.

Command Executed:

```powershell
Set-MpPreference -DisableRealtimeMonitoring $true
```

After validation, Microsoft Defender protection was restored.

```powershell
Set-MpPreference -DisableRealtimeMonitoring $false
```

The activity generated a registry modification event associated with Microsoft Defender configuration changes.

## Detection

The detection monitors registry modifications affecting Microsoft Defender security settings.

Detection Logic:

* Monitor registry modification events
* Detect changes to Defender real-time protection settings
* Identify modifications to the `DisableRealtimeMonitoring` registry value

Registry Path Observed:

```text
HKLM\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection\DisableRealtimeMonitoring
```

This behavior may indicate an attempt to weaken endpoint security controls prior to executing malicious activity.

## Validation Results

The simulation successfully generated registry modification telemetry on the endpoint.

Security Onion ingested the resulting events and the Sigma rule generated an alert when the Defender configuration change was observed.

The generated telemetry provided visibility into:

* Registry Path
* Registry Value
* Executing User
* Associated Process
* Event Timestamp

## Hunt Query

```kql
*DisableRealtimeMonitoring*
```

This query was used to identify registry modifications associated with Microsoft Defender real-time protection settings. The hunt query successfully identified the Atomic simulation and validated telemetry visibility within Security Onion.

## Evidence

The following screenshots were captured during testing and validation:

1. PowerShell command execution.
2. Security Onion Hunt results.
3. Registry modification event details.
4. Detection alert generated from the Sigma rule.

Screenshots are available in the `screenshots/` directory.

## Key Takeaways

Disabling or modifying security controls is a common defense evasion technique used by adversaries to reduce the likelihood of detection.

Monitoring Microsoft Defender configuration changes through registry activity provides visibility into attempts to impair endpoint security and can help identify attacker actions prior to malware execution.

## References

* MITRE ATT&CK T1562.001 – Impair Defenses
* Microsoft Defender Documentation
* Security Onion
* Sigma

