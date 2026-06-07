# T1082 - System Information Discovery

## Summary

System information discovery is commonly performed by attackers shortly after gaining access to a host. The objective is to gather basic information about the system, including the current user, hostname, operating system version, and system configuration.

For this detection, I simulated system discovery activity using common Windows utilities such as `whoami`, `hostname`, and `systeminfo`. I then analyzed the resulting Sysmon telemetry and created a Sigma rule to identify these commands when executed from common command interpreters and scripting engines.



## Attack Simulation

To simulate system discovery activity, I executed the following commands from the Windows endpoint:

```cmd
whoami
hostname
systeminfo
```

These commands are commonly used by both administrators and adversaries to gather information about a host. The objective was to generate telemetry and validate that the detection successfully identified the activity.

## Detection

The detection monitors process creation events and looks for execution of common discovery utilities including:

* whoami.exe
* hostname.exe
* systeminfo.exe

To reduce noise, the rule only triggers when these processes are launched from common command interpreters or scripting engines such as PowerShell, Command Prompt, Windows Script Host, or Microsoft Word.

## Validation Results

The detection was validated by executing the test commands on the Windows endpoint and reviewing the resulting telemetry in Security Onion.

The following commands were successfully detected:

| Command    | Result   |
| ---------- | -------- |
| whoami     | Detected |
| hostname   | Detected |
| systeminfo | Detected |

All executions generated Sysmon Event ID 1 (Process Creation) events and were visible within Security Onion Hunt.

The Sigma rule successfully matched the expected process and parent process relationships during testing.

## Key Takeaways

This exercise demonstrated how common system discovery commands appear within endpoint telemetry and how they can be identified using process creation events.

While these commands are frequently used by administrators, they can also provide valuable indicators during the early stages of an intrusion when analyzed alongside parent process information and surrounding activity.

## References

* MITRE ATT&CK T1082 – System Information Discovery
* Sigma Detection Rules
* Sysmon Event ID 1 – Process Creation


