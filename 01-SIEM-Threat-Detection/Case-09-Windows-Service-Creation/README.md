# Case 09 - Windows Service Creation

## Objective

Detect and investigate Windows service creation activity using Elastic Stack and Windows Event Logs.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

A new Windows service was created using sc.exe. Adversaries commonly create malicious services to establish persistence and maintain access to compromised systems.

## Command Used

```cmd
sc.exe create BackupService binPath= "C:\Windows\System32\notepad.exe"
```

## Detection Method

Windows Event ID 7045 (A service was installed in the system)

## Findings

* Service Name: BackupService
* Service Binary: C:\Windows\System32\notepad.exe
* Hostname: WINDOWS10

## MITRE ATT&CK

* T1543.003 - Create or Modify System Process: Windows Service

## References

* Investigation.md
* MITRE-Mapping.md
