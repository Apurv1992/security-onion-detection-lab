# T1082 - System Information Discovery

## Summary

System information discovery is commonly performed by attackers shortly after gaining access to a host. The objective is to gather basic information about the system, including the current user, hostname, operating system version, and system configuration.

For this detection, I simulated system discovery activity using common Windows utilities such as `whoami`, `hostname`, and `systeminfo`. I then analyzed the resulting Sysmon telemetry and created a Sigma rule to identify these commands when executed from common command interpreters and scripting engines.
