# Investigation Report

## Alert Summary

Wazuh generated alerts indicating sudo activity on the monitored Linux endpoint.

---

## Investigation Steps

### Step 1 - Review Alert

The alert indicated that a command was executed using sudo privileges.

---

### Step 2 - Identify User

The account responsible for the activity was identified from the event logs.

Information reviewed:

- Username
- Hostname
- Timestamp

---

### Step 3 - Analyze Command Execution

The executed command was reviewed to determine whether administrative privileges were required.

Observed examples:

- sudo su
---

### Step 4 - Determine Impact

Privilege escalation activity was successfully performed.

Although this activity was generated in a controlled lab environment, similar behavior may indicate attacker attempts to gain administrative access.

---

## Classification

Suspicious

---

## MITRE ATT&CK

- T1548.003 - Sudo and Sudo Caching

---

## Conclusion

Wazuh successfully detected sudo-based privilege escalation activity.

The generated alerts provide visibility into administrative actions performed on Linux endpoints and can help analysts identify potential privilege escalation attempts.
