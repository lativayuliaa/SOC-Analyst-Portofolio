# Investigation Report

## Summary

PowerShell activity was detected on the Windows 10 host. Sysmon recorded the process creation event and provided visibility into the executed command line and parent-child process relationship.

## Timeline

1. User launched PowerShell.
2. Sysmon generated Event ID 1.
3. Winlogbeat forwarded the event to Elasticsearch.
4. Kibana was used to investigate the process details.

## Hostname

WINDOWS10

## User

vboxuser

## Process Name

powershell.exe

## Parent Process

explorer.exe

## Command Line

```powershell
powershell.exe -nop -c "Get-Process"
```

## Evidence

* Sysmon Event ID 1

## Findings

PowerShell execution was successfully detected and analyzed. The presence of parameters such as `-nop` and `-w hidden` may indicate suspicious activity and should be monitored closely in enterprise environments.

## MITRE ATT&CK

T1059.001 - PowerShell

## Severity

Medium

## Recommendations

* Monitor PowerShell activity.
* Enable Sysmon process creation logging.
* Create alerts for suspicious PowerShell arguments.
* Investigate hidden or encoded PowerShell commands.
