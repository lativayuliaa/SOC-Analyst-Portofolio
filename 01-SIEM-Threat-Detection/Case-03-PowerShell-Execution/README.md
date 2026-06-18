# Case 03 - PowerShell Execution

## Objective

Detect and investigate PowerShell execution activity using Sysmon and Elastic Stack.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

A PowerShell command was executed on the Windows host. The activity was captured by Sysmon and forwarded to Elasticsearch using Winlogbeat.

## Commands Used

```powershell
powershell.exe -nop -c "Get-Process"
```

```powershell
powershell.exe -nop -w hidden -c "Get-Date"
```

## Detection Method

Sysmon Event ID 1 (Process Creation)

## Observed Artifacts

* powershell.exe
* Command line arguments
* Parent process
* Username
* Hostname

## Findings

* Process Name: powershell.exe
* Parent Process: explorer.exe
* Hostname: WINDOWS10
* User: vboxuser

## MITRE ATT&CK

* T1059.001 - PowerShell

## References

* Investigation/investigation.md
* MITRE-Mapping/mitre-mapping.md
