# MITRE ATT&CK Mapping

## Technique

### T1110 - Brute Force

Attackers may attempt to gain access by repeatedly guessing passwords until a valid credential is found.

---

## Tactic

### Credential Access

The objective of the attacker is to obtain valid credentials for authentication.

---

## Detection Evidence

Observed Indicators:

- Multiple failed authentication attempts
- Repeated password validation failures
- PAM authentication errors

---

## Detection Source

- Linux Authentication Logs
- PAM Logs
- Wazuh Security Alerts
