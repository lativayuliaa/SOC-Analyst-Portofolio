# Case 05 - New User Creation

## Objective

Detect and investigate the creation of a new local user account on a Windows 10 host using Elastic Stack and Windows Security Event Logs.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

A new local account was created on the Windows system. This technique is commonly used by attackers to establish persistence and maintain access to compromised systems.

## Command Used

```cmd
net user backupadmin "input your password" /add
```

## Detection Method

Windows Security Event ID 4720 (User Account Created)

## Findings

* New User: backupadmin
* Creator Account: vboxuser
* Hostname: WINDOWS10

## MITRE ATT&CK

* T1136.001 - Create Account: Local Account

## References

* Investigation.md
* MITRE-Mapping.md
