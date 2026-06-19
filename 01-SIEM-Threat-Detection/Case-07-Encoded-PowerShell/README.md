# Case 07 - Encoded PowerShell

## Objective

Detect and investigate Base64-encoded PowerShell execution using Sysmon and Elastic Stack.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

A Base64-encoded PowerShell command was executed on the Windows host. Encoded PowerShell commands are frequently used by adversaries to obfuscate malicious activity and evade detection.

## Commands Used

### Generate Base64 Command

```powershell
$command = "Get-Process"
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encoded = [Convert]::ToBase64String($bytes)
$encoded
```

### Execute Encoded Command

```powershell
powershell.exe -enc RwBlAHQALQBQAHIAbwBjAGUAcwBzAA==
```

## Detection Method

Sysmon Event ID 1 (Process Creation)

## Findings

* Process Name: powershell.exe
* Command Argument: -enc
* User: vboxuser
* Hostname: WINDOWS10

## MITRE ATT&CK

* T1059.001 - PowerShell

## References

* Investigation.md
* MITRE-Mapping.md
