# T1218.011 - Rundll32

## Summary

Rundll32 is a legitimate Windows utility used to execute functions exported from Dynamic Link Libraries (DLLs). Adversaries can abuse Rundll32 to execute malicious code while leveraging a trusted Microsoft-signed binary.

For this detection, Atomic Red Team was used to simulate Rundll32 execution on a Windows endpoint. The resulting telemetry was analyzed in Security Onion and a Sigma rule was developed to detect the behavior.

## Attack Simulation

Atomic Red Team technique T1218.011 was executed on the Windows endpoint to simulate Signed Binary Proxy Execution using Rundll32.

The test leveraged Rundll32 to execute a DLL function, generating process creation telemetry that was collected and analyzed within Security Onion.

## Detection

The detection monitors process creation events involving Rundll32 and identifies suspicious execution activity associated with Signed Binary Proxy Execution.

Detection Logic:

* Identify Rundll32 execution events
* Monitor child processes spawned by Rundll32
* Capture command-line arguments used during execution
* Alert on suspicious process relationships involving Rundll32

This detection focuses on behavioral activity rather than specific malicious DLLs, improving resilience against variations in attacker tooling.

## Validation Results

The Atomic Red Team simulation successfully generated process creation telemetry on the endpoint.

Security Onion ingested the resulting events and the Sigma rule generated an alert when Rundll32 execution activity was observed.

The generated telemetry provided visibility into:

* Parent Process
* Child Process
* Executing User
* Command Line Arguments
* Process Creation Events

## Hunt Query

```kql
process.parent.name:rundll32.exe
AND NOT process.name:rundll32.exe
```

This query identifies child processes launched by Rundll32. Adversaries frequently abuse Rundll32 as a trusted Windows binary to proxy execution and evade security controls.

The hunt query successfully identified the Atomic Red Team simulation and validated telemetry visibility within Security Onion.

## Evidence

The following screenshots were captured during testing and validation:

1. Atomic Red Team execution.
2. Security Onion Hunt results.
3. Detection alert generated from the Sigma rule.

Screenshots are available in the `screenshots/` directory.

## Key Takeaways

Rundll32 is a trusted Windows utility that is commonly abused by attackers to execute malicious code while blending in with legitimate operating system activity.

Monitoring Rundll32 execution and associated child processes can provide valuable visibility into defense evasion and execution techniques used by adversaries.

## References

* MITRE ATT&CK T1218.011 – Rundll32
* Atomic Red Team
* Security Onion
* Sigma

