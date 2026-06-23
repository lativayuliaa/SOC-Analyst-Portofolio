# Suspicious Sudo Activity

## Overview

This case demonstrates how Wazuh detects privilege escalation activities performed through the Linux sudo utility.

The sudo command allows users to execute commands with elevated privileges. Attackers frequently abuse sudo to gain administrative access and perform unauthorized actions on Linux systems.

---

## Scenario

A privileged command was executed using sudo on the monitored Kali Linux endpoint.

The objective was to verify that Wazuh successfully collected and generated alerts related to sudo activity.

---

## Attack Simulation

The following command was executed:

```bash
sudo su
```

## Detection Method

Wazuh monitored Linux authentication and privilege escalation logs and generated alerts when sudo activity occurred.

Relevant log sources:

- auth.log
- sudo logs
- PAM logs

---

## Findings

Wazuh successfully detected sudo execution events.

Observed information:

- User account
- Hostname
- Command executed
- Timestamp
- Privilege escalation activity

---

## Security Impact

Abnormal sudo activity may indicate:

- Privilege escalation attempts
- Unauthorized administrative access
- Insider threats
- Post-compromise attacker activity

---

## Outcome

The objective was successfully completed.

Wazuh generated alerts and provided visibility into privileged command execution on the Linux endpoint.

---
