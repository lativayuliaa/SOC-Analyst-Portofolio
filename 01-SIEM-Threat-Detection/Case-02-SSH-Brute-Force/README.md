# Case 02 - SSH Brute Force Detection

## Objective

Detect and investigate SSH brute-force activity against a Windows 10 host using Elastic Stack and Windows Security Event Logs.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Kali Linux  | Attacker         | 192.168.56.102 |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

An attacker performed multiple SSH login attempts against the victim machine using Hydra. Several authentication attempts failed before valid credentials were discovered, resulting in a successful login.

## Attack Command

```bash
hydra -l vboxuser -P pass.txt ssh://192.168.56.103
```

## Observed Events

* Event ID 4625 – Failed Logon
* Event ID 4624 – Successful Logon

## Detection Method

Windows Security Event Logs were collected using Winlogbeat and analyzed in Kibana.

## Findings

* Source IP: 192.168.56.102
* Destination IP: 192.168.56.103
* Target User: vboxuser
* Hostname: WINDOWS10

## MITRE ATT&CK

* T1110 - Brute Force

## References

* Investigation/investigation.md
* MITRE-Mapping/mitre-mapping.md
