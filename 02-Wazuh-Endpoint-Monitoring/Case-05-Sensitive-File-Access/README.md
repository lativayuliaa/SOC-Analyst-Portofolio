# Sensitive File Access

## Overview

This case demonstrates how Wazuh can be used to monitor access attempts against sensitive Linux credential files.

Files such as `/etc/passwd` and `/etc/shadow` contain account information and password hashes that are frequently targeted by attackers during post-exploitation activities.

---

## Scenario

Sensitive credential files were accessed from the monitored Kali Linux endpoint.

The objective was to simulate attacker behavior and validate visibility into attempts to access credential-related files.

---

## Attack Simulation

The following commands were executed:

```bash
cat /etc/passwd

sudo cat /etc/shadow
```

These commands were used to access user account information and password hash data.

---

## Detection Method

Wazuh monitored endpoint activity and file-related events associated with sensitive system files.

Relevant monitored assets:

* /etc/passwd
* /etc/shadow

---

## Findings

Sensitive credential files were successfully accessed during the simulation.

Observed information:

* User account
* Hostname
* Timestamp
* File accessed
* Command executed

---

## Security Impact

Unauthorized access to credential files may indicate:

* Credential harvesting
* Privilege escalation preparation
* Password hash collection
* Post-exploitation activity

---

## Outcome

The objective was successfully completed.

The activity demonstrates how attackers may attempt to gather credential-related information from Linux systems after obtaining access.

---
