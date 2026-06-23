# Authentication Failures Detection

## Overview

This case demonstrates how Wazuh detects failed authentication attempts on a Linux endpoint.

Authentication failures are common indicators of password guessing, brute force attempts, or unauthorized access attempts. Monitoring these events helps security analysts identify suspicious login behavior before an attacker successfully gains access.

---

## Scenario

Multiple failed authentication attempts were generated on the Kali Linux endpoint using incorrect credentials.

The objective was to verify that Wazuh successfully collected and generated alerts for authentication failures.

---

## Attack Simulation

The following command was executed:

```bash
su root
```

Invalid passwords were entered multiple times to generate failed authentication events.

---

## Detection Method

Wazuh collected authentication logs from the Linux endpoint and generated security alerts related to failed login attempts.

Relevant log sources:

- auth.log
- PAM authentication logs
- Linux authentication events

---

## Findings

Wazuh successfully detected multiple failed authentication attempts and generated corresponding alerts.

Observed information:

- Target account
- Hostname
- Timestamp
- Authentication failure events

---

## Security Impact

Repeated authentication failures may indicate:

- Password guessing attacks
- Brute force activity
- Unauthorized access attempts
- Credential abuse

---

## Outcome

The objective was successfully completed.

Authentication failure events were detected and logged by Wazuh for further investigation.

---
