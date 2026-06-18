# Case 01 - Nmap Detection

## Objective

Detect and investigate network reconnaissance activity performed against a Windows 10 host using Nmap.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Kali Linux  | Attacker         | 192.168.56.102 |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

The attacker machine performed an Nmap scan against the Windows host to identify open ports and services.

## Command Used

```bash
sudo nmap -A 192.168.56.103
```

## Detection Method

Sysmon Event ID 3 (Network Connection)

## Findings

* Source IP: 192.168.56.102
* Destination IP: 192.168.56.103
* Victim Hostname: WINDOWS10

## MITRE ATT&CK

* T1046 - Network Service Discovery

## References

* Investigation/investigation.md
* MITRE-Mapping/mitre-mapping.md
