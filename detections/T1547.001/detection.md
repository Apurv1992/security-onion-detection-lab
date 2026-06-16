# T1547.001 - Registry Run Keys / Startup Folder

## Summary

Registry Run Keys are a commonly abused persistence mechanism that allows programs to execute automatically when a user logs on to a Windows system.

For this detection, Atomic Red Team was used to simulate persistence through modification of Windows Run registry keys. The resulting telemetry was analyzed in Security Onion and a Sigma rule was developed to detect the activity.

## Attack Simulation

Atomic Red Team technique T1547.001 was executed on the Windows endpoint to simulate persistence using Registry Run Keys.

The test modified registry locations commonly associated with automatic program execution during user logon.

Example registry locations:

```text
HKCU\Software\Microsoft\Windows\CurrentVersion\Run

HKLM\Software\Microsoft\Windows\CurrentVersion\Run
```

## Detection

The detection monitors modifications to Windows Run and RunOnce registry keys that are frequently used by attackers to maintain persistence.

Detection Logic:

* Monitor registry modifications to Run and RunOnce keys
* Identify newly created or modified registry values
* Alert when persistence-related registry locations are altered

## Validation Results

The Atomic Red Team test successfully generated registry modification activity on the endpoint.

Security Onion ingested the resulting telemetry and the Sigma rule generated an alert when the registry key was modified.

The generated telemetry provided visibility into:

* Registry Path
* Modified Registry Value
* User Account
* Associated Process

## Hunt Query

```kql
process.name:reg.exe AND process.command_line:*CurrentVersion\\Run*
```

## Evidence

The following screenshots were captured during testing and validation:

1. Atomic Red Team execution.
2. Security Onion Hunt results showing the registry modification.
3. Detection alert generated from the Sigma rule.

Screenshots are available in the `screenshots/` directory.

## Key Takeaways

Registry Run Keys remain a popular persistence mechanism because they are simple to implement and blend into normal operating system behavior.

Monitoring modifications to these registry locations can help identify attempts to establish persistence and maintain long-term access on Windows systems.

## References

* MITRE ATT&CK T1547.001 – Registry Run Keys / Startup Folder
* Atomic Red Team
* Security Onion
* Sigma

