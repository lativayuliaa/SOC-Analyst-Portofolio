# MITRE ATT&CK Mapping

## Technique

### T1548.003 - Sudo and Sudo Caching

Adversaries may perform privilege escalation by abusing sudo permissions to execute commands as another user, typically root.

---

## Tactic

### Privilege Escalation

The attacker attempts to gain elevated permissions on the target system.

---

## Detection Evidence

Observed Indicators:

- Sudo command execution
- Privileged command usage
- Root-level access requests

---

## Detection Source

- Linux Authentication Logs
- Sudo Logs
- PAM Logs
- Wazuh Security Alerts
