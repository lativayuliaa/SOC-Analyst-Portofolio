# Investigation Report

## Alert Summary

Root-level administrative activity was observed on the monitored Linux endpoint.

The activity involved elevated privilege usage and execution of administrative commands.

---

## Investigation Steps

### Step 1 - Review Alert

The alert indicated that privileged commands were executed after elevation to root privileges.

---

### Step 2 - Identify User

The responsible account was identified using authentication and sudo-related events.

Information reviewed:

- Username
- Hostname
- Timestamp

---

### Step 3 - Analyze Activity

The following activities were observed:

- Root shell access
- User identity verification
- Access to sensitive credential files

Observed commands:

```bash
sudo su
id
whoami
cat /etc/shadow
```

---

### Step 4 - Determine Impact

The activity demonstrates successful execution of commands using elevated privileges.

In a real-world environment, similar behavior may indicate:

- Privilege escalation
- Credential harvesting
- System manipulation
- Persistence preparation

---

## Classification

Suspicious

---

## MITRE ATT&CK

- T1078 - Valid Accounts
- T1548.003 - Sudo and Sudo Caching

---

## Conclusion

Root-level activity was successfully observed and monitored through Wazuh.

The collected telemetry provides valuable visibility into privileged actions and can help security analysts detect post-exploitation activity on Linux endpoints.
