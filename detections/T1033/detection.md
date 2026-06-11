# T1033 - Account Discovery

## Summary

Account discovery is a common reconnaissance activity performed by attackers after gaining access to a system. The objective is to identify local and domain users, understand account privileges, and gather information that may assist with privilege escalation or lateral movement.

For this detection, I simulated account enumeration activity on a Windows endpoint and analyzed the resulting telemetry in Security Onion. The goal was to identify common account discovery commands using process creation events.

## Attack Simulation

The following commands were executed from the Windows endpoint:

```cmd
whoami /all

net user

net user /domain

query user
```

These commands are frequently used by administrators but are also commonly observed during post-compromise reconnaissance activities.

## Detection

The detection monitors process creation events and looks for account enumeration commands, including:

* whoami.exe
* net.exe
* query.exe

The rule also examines command-line arguments associated with user enumeration such as:

* user
* /all
* /domain

To provide additional context, the detection focuses on commands launched from common shells and scripting engines such as Command Prompt and PowerShell.

## Validation Results

The test commands generated Sysmon Process Creation (Event ID 1) telemetry and were successfully ingested into Security Onion.

The Sigma rule successfully identified the account discovery activity and provided visibility into:

* Executing user
* Command-line arguments
* Parent process
* Host information

## Hunt Query

```kql
event.code:1 AND
process.name:(whoami.exe OR net.exe OR query.exe)
```

## Key Takeaways

Account discovery often occurs early in an attack lifecycle as adversaries attempt to understand the environment and identify potential targets.

While these commands are commonly used for legitimate administrative purposes, analyzing the execution context, parent process, and surrounding activity can help distinguish normal administration from suspicious reconnaissance behavior.

