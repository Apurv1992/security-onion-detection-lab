# T1218.010 - Regsvr32

## Summary

Regsvr32 is a legitimate Windows utility used to register and unregister DLLs. Adversaries can abuse Regsvr32 to execute scripts and payloads while bypassing application controls, a technique commonly known as Signed Binary Proxy Execution.

For this detection, Atomic Red Team was used to simulate Regsvr32 abuse on a Windows endpoint. The resulting telemetry was analyzed in Security Onion and a Sigma rule was developed to detect the behavior.

## Attack Simulation

Atomic Red Team technique T1218.010 was executed on the Windows endpoint to simulate malicious use of Regsvr32.

The test leveraged Regsvr32 to execute a payload, resulting in the creation of a child process.

Observed Process Chain:

```text
regsvr32.exe → calc.exe
```

This behavior is commonly associated with attacker attempts to proxy execution through trusted Windows binaries.

## Detection

The detection monitors process creation events where Regsvr32 spawns a child process.

Detection Logic:

* Identify Regsvr32 execution
* Monitor child processes created by Regsvr32
* Alert on suspicious process chains originating from Regsvr32

This detection focuses on behavioral activity rather than specific command-line arguments, making it more resilient against variations in attacker tooling.

## Validation Results

The Atomic Red Team simulation successfully generated process creation telemetry on the endpoint.

Security Onion ingested the resulting events and the Sigma rule generated an alert when Regsvr32 spawned a child process.

The generated telemetry provided visibility into:

* Parent Process
* Child Process
* Executing User
* Command Line Arguments
* Process Creation Events

## Hunt Query

```kql
process.parent.name:regsvr32.exe
AND NOT process.name:regsvr32.exe
```

This query identifies child processes launched by Regsvr32. During testing, the query successfully identified the Atomic Red Team simulation and validated telemetry visibility within Security Onion.

## Evidence

The following screenshots were captured during testing and validation:

1. Atomic Red Team execution.
2. Security Onion Hunt results showing Regsvr32 spawning a child process.
3. Detection alert generated from the Sigma rule.

Screenshots are available in the `screenshots/` directory.

## Key Takeaways

Regsvr32 is a trusted Windows binary that can be abused to execute malicious content while blending in with legitimate operating system activity.

Monitoring child processes spawned by Regsvr32 can provide visibility into Signed Binary Proxy Execution techniques and help detect defense evasion and execution activity.

## References

* MITRE ATT&CK T1218.010 – Regsvr32
* Atomic Red Team
* Security Onion
* Sigma

