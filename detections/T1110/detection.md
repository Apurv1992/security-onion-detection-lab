# T1110 - Brute Force

## Summary

Brute force attacks are a common technique used by adversaries to gain access to valid accounts through repeated authentication attempts. Excessive failed logons against a user account can indicate password guessing, automated attacks, or attempts to gain unauthorized access.

For this detection, I simulated multiple failed logon attempts against a domain user account within my lab environment and analyzed the resulting Windows Security Event logs in Security Onion. The objective was to identify authentication failures that exceeded a predefined threshold and could indicate potential brute force activity.

## Attack Simulation

To generate authentication failures, I attempted to log in to a domain user account multiple times using an incorrect password.

The activity generated Windows Security Event ID 4625 (Failed Logon) events on the Domain Controller.

This simulation was performed to validate the detection's ability to identify repeated authentication failures against the same account.

## Detection

The detection monitors Windows Security Event ID 4625 and identifies user accounts that experience more than five failed logon attempts within a five-minute period.

Detection Logic:

* Event ID: 4625
* Group By: User Account
* Threshold: More than 5 Failed Logons
* Time Window: 5 Minutes

The threshold helps reduce noise from occasional authentication mistakes while highlighting activity that may warrant further investigation.

## Validation Results

The simulated failed logon attempts generated the expected Windows Security events and were successfully ingested into Security Onion.

During testing, the detection correctly identified accounts that exceeded the configured threshold and generated an alert for analyst review.

The alert provided visibility into:

* Target User Account
* Source Workstation
* Logon Type
* Authentication Failure Details
* Event Timeline

## Hunt Query

```kql
event.code:4625
```

## Investigation Notes

When investigating repeated failed logons, the following questions may help determine whether the activity is malicious or benign:

* Is the activity targeting a single account or multiple accounts?
* Is the source workstation expected to authenticate to the target account?
* Are there successful logons following the failed attempts?
* Is the activity occurring outside normal business hours?
* Is the account associated with a privileged user?

Additional context from authentication logs, endpoint telemetry, and user activity should be reviewed before determining the severity of the event.

## Key Takeaways

Authentication failures are common in enterprise environments and are not inherently suspicious. However, a high volume of failed logon attempts against the same account within a short period may indicate brute force activity and should be investigated.

This exercise provided hands-on experience with Windows authentication telemetry, threshold-based detections, and Security Onion alert validation while reinforcing the importance of monitoring account access activity within an Active Directory environment.

## References

* MITRE ATT&CK T1110 – Brute Force
* Windows Security Event ID 4625 – Failed Logon
* Security Onion

