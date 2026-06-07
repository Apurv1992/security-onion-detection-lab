# T1059.001 - PowerShell

## Summary

PowerShell is one of the most commonly abused tools in Windows environments due to its ability to execute commands, automate tasks, and interact with system components. It is frequently used by attackers for reconnaissance, execution, persistence, and post-exploitation activities.

For this detection, I simulated PowerShell execution within my lab environment and analyzed the resulting telemetry in Security Onion. The objective was to identify potentially suspicious PowerShell activity based on command-line arguments commonly associated with attacker tradecraft.

## Attack Simulation

The following commands were executed on the Windows endpoint:

```powershell
powershell.exe Get-Process

powershell.exe -nop -c "Get-Process"

powershell.exe -ExecutionPolicy Bypass Get-Service
```

These commands were chosen to generate process creation telemetry and validate detection coverage for common PowerShell execution patterns.

## Detection

The detection monitors PowerShell process creation events and looks for command-line arguments that are frequently observed in malicious activity, including:

* `-nop`
* `-encodedcommand`
* `-enc`
* `-ExecutionPolicy Bypass`
* `-w hidden`

The goal is to identify suspicious PowerShell execution while providing analysts with sufficient context for investigation.

## Validation Results

The test commands generated Sysmon Process Creation (Event ID 1) telemetry and were successfully ingested into Security Onion.

The Sigma rule successfully identified PowerShell executions containing suspicious command-line arguments and provided visibility into:

* User context
* Parent process
* Command-line arguments
* Host information

## Hunt Query

```kql
event.code:1 AND process.name:(powershell.exe OR pwsh.exe)
```

Additional filtering can be applied to identify encoded commands, hidden windows, or execution policy bypass attempts.

## Key Takeaways

PowerShell is a legitimate administrative tool, making context critical during investigations. While the execution of PowerShell alone is not necessarily suspicious, command-line arguments, parent processes, and surrounding activity can help distinguish normal administration from potentially malicious behavior.

This exercise helped reinforce the importance of command-line visibility and process creation telemetry when building detections for PowerShell-based activity.

