# Detection Rules

## Risk Score Engine

The workflow prioritizes Windows security events using a custom risk score model.

| Event ID | Detection | Risk |
|----------|-----------|-----:|
| 4625 | Failed Login | 40 |
| 4720 | New User Created | 60 |
| 4104 | Encoded PowerShell | 90 |
| 10 (Sysmon) | Mimikatz | 100 |

Risk scores greater than or equal to 60 are treated as security incidents.

---

## Brute Force Detection

The workflow performs event correlation for Windows Event ID 4625.

Detection Rule:

- Event ID = 4625
- Failed Login Count ≥ 5

Result:

- Create Jira Security Incident
- Execute Automated Response

---

## MITRE ATT&CK Mapping

| Technique | ID |
|-----------|----|
| Brute Force | T1110 |
| Create Account | T1136 |
| PowerShell | T1059.001 |
| Credential Dumping | T1003 |

---

## Automated Response

The workflow currently supports:

- Disable suspicious local user account (Proof of Concept)

Future implementation:

- Firewall Blocking
- Endpoint Isolation
- Account Lockout
- Email Notification
- Slack Integration

---

## Limitations

Current implementation is designed as a laboratory proof of concept.

Some attack scenarios, such as SSH brute force, may not expose the attacker's source IP address depending on Windows Event Log behavior. In those situations, the workflow demonstrates automated response using the available event information.
