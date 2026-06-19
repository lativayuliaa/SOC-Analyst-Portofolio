# Investigation Report

## Summary

Windows service creation activity was detected on the Windows 10 host. A new service named BackupService was installed and configured to execute notepad.exe. Service creation events are frequently associated with persistence mechanisms used by malware and threat actors.

## Timeline

1. A service creation command was executed.
2. Windows generated Event ID 7045.
3. Winlogbeat forwarded the event to Elasticsearch.
4. Kibana was used to investigate the event details.

## Hostname

WINDOWS10

## Service Name

BackupService

## Service Binary

C:\Windows\System32\notepad.exe

## Command Used

```cmd
sc.exe create BackupService binPath= "C:\Windows\System32\notepad.exe"
```

## Evidence

### Event ID 7045

A service was installed in the system

## Findings

The observed activity is consistent with Windows service creation. Similar techniques are commonly used by malware and adversaries to establish persistence and execute malicious binaries automatically.

## MITRE ATT&CK

T1543.003 - Create or Modify System Process: Windows Service

## Severity

Medium

## Recommendations

* Monitor service installation events.
* Investigate newly created services.
* Alert on unusual service binaries and paths.
* Review service creation activity performed by non-administrative users.
* Correlate service creation events with process execution and network activity.
