# Investigation Report

## Summary

PowerShell download activity was detected on the Windows 10 host. The victim system established a connection to the Kali Linux machine and downloaded a file using Invoke-WebRequest.

## Timeline

1. Kali Linux hosted a file using Python HTTP Server.
2. PowerShell was launched on Windows 10.
3. Invoke-WebRequest downloaded the file.
4. Sysmon generated Event ID 1 and Event ID 3.
5. Winlogbeat forwarded the logs to Elasticsearch.
6. Kibana was used to investigate the activity.

## Source IP

192.168.56.103

## Destination IP

192.168.56.102

## Hostname

WINDOWS10

## User

vboxuser

## Process Name

powershell.exe

## Command Line

```powershell
powershell.exe -nop -c "Invoke-WebRequest http://192.168.56.102:8000/test.txt -OutFile C:\Temp\test.txt"
```

## Evidence

### Sysmon Event ID 1

Process Creation

### Sysmon Event ID 3

Network Connection

## Findings

The activity is consistent with a file transfer operation performed through PowerShell. Similar techniques are frequently used by adversaries to retrieve payloads and establish command-and-control capabilities.

## MITRE ATT&CK

* T1059.001 - PowerShell
* T1105 - Ingress Tool Transfer

## Severity

Medium

## Recommendations

* Monitor PowerShell execution.
* Alert on Invoke-WebRequest activity.
* Inspect outbound connections initiated by PowerShell.
* Restrict PowerShell usage where possible.
* Monitor file downloads from untrusted hosts.
