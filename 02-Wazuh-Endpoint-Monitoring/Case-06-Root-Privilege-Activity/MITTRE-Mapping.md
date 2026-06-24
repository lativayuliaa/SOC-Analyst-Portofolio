# MITRE ATT&CK Mapping

## Technique 1

### T1078 - Valid Accounts

Adversaries may use valid accounts to gain and maintain access to systems while appearing as legitimate users.

---

## Technique 2

### T1548.003 - Sudo and Sudo Caching

Adversaries may abuse sudo permissions to execute commands with elevated privileges.

---

## Tactic

### Privilege Escalation

The attacker attempts to obtain elevated permissions on the target system.

### Defense Evasion

Legitimate administrative tools may be abused to blend malicious activity with normal operations.

---

## Detection Evidence

Observed Indicators:

- Root shell activity
- Privileged command execution
- Sudo usage
- Access to sensitive files

---

## Detection Source

- Linux Authentication Logs
- PAM Logs
- Sudo Logs
- Wazuh Security Alerts
