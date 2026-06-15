# T1053.005 - Scheduled Task Creation

## Summary

Scheduled Tasks are commonly used by administrators to automate recurring activities. However, adversaries frequently abuse scheduled tasks to establish persistence, execute malicious payloads, or maintain access to compromised systems.

For this detection, I simulated scheduled task creation on a Windows endpoint and analyzed the resulting telemetry in Security Onion. The objective was to identify task creation activity that could indicate persistence or unauthorized execution.

## Attack Simulation

To simulate the technique, I created a scheduled task using the Windows `schtasks.exe` utility.

Example command:

```cmd
schtasks /create /tn TestTask /tr "powershell.exe" /sc onlogon
```

The task was configured to execute PowerShell whenever a user logged on to the system.

## Detection

The detection monitors process creation events and identifies executions of `schtasks.exe` containing the `/create` argument.

Detection Logic:

* Process Name: `schtasks.exe`
* Command Line Contains: `/create`

This approach provides visibility into scheduled task creation activity and can help identify potential persistence mechanisms.

## Validation Results

The scheduled task was successfully created on the Windows endpoint and generated process creation telemetry.

Security Onion successfully ingested the event and the Sigma rule generated an alert when the scheduled task creation command was executed.

The resulting telemetry provided visibility into:

* Executing User
* Parent Process
* Command Line Arguments
* Scheduled Task Creation Activity

## Hunt Query

```kql
process.name:schtasks.exe AND process.command_line:*create*
```

## Evidence

The following screenshots were captured during testing and validation:

1. Security Onion Hunt showing the scheduled task creation event.
2. Detection alert generated from the Sigma rule.

Screenshots are available in the `screenshots/` directory for this detection.

## Key Takeaways

Scheduled Tasks are a legitimate administrative feature but are also commonly abused by attackers for persistence and execution.

Monitoring task creation activity provides defenders with visibility into potentially suspicious automation and persistence mechanisms. Additional context such as the task name, execution command, and parent process should be reviewed to determine whether the activity is expected or malicious.

## References

* MITRE ATT&CK T1053.005 – Scheduled Task
* Microsoft Schtasks Utility Documentation
* Security Onion

