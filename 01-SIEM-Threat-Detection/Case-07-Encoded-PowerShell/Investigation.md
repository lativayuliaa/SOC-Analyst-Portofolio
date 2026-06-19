# Investigation Report

## Summary

Encoded PowerShell execution was detected on the Windows 10 host. Sysmon recorded the process creation event, allowing visibility into the command-line arguments and execution details.

## Timeline

1. A command was converted into Base64 format.
2. PowerShell executed the encoded command.
3. Sysmon generated Event ID 1.
4. Winlogbeat forwarded the event to Elasticsearch.
5. Kibana was used to investigate the activity.

## Hostname

WINDOWS10

## User

vboxuser

## Process Name

powershell.exe

## Command Line

```powershell
powershell.exe -enc RwBlAHQALQBQAHIAbwBjAGUAcwBzAA==
```

## Evidence

### Sysmon Event ID 1

Process Creation

## Findings

The observed activity is consistent with encoded PowerShell execution. Although the command executed in this lab was benign, encoded commands are widely used by malware, ransomware, and advanced threat actors to obfuscate malicious actions.

## MITRE ATT&CK

T1059.001 - PowerShell

## Severity

Medium

## Recommendations

* Monitor PowerShell command-line arguments.
* Alert on the use of -enc and -EncodedCommand parameters.
* Investigate unusual parent-child process relationships.
* Correlate PowerShell execution with network connections and file creation events.
* Restrict PowerShell usage where appropriate.
