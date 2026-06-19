# Investigation Report

## Summary

Execution of the Windows LOLBin `certutil.exe` was detected on the Windows 10 host. Sysmon recorded the process creation event and provided visibility into the executed command line and parent process.

## Timeline

1. The user executed certutil.exe.
2. Sysmon generated Event ID 1.
3. Winlogbeat forwarded the event to Elasticsearch.
4. Kibana was used to investigate the activity.

## Hostname

WINDOWS10

## User

vboxuser

## Process Name

certutil.exe

## Parent Process

cmd.exe

## Command Line

```cmd
certutil.exe -hashfile C:\Windows\System32\notepad.exe SHA256
```

## Evidence

### Sysmon Event ID 1

Process Creation

## Findings

The activity is consistent with LOLBin usage. Although the observed command is benign, adversaries frequently abuse certutil.exe to download payloads, encode data, and evade detection.

## MITRE ATT&CK

T1218 - System Binary Proxy Execution

## Severity

Medium

## Recommendations

* Monitor LOLBin execution.
* Create alerts for suspicious certutil.exe activity.
* Investigate unusual parent-child process relationships.
* Review command-line arguments associated with LOLBins.
* Correlate LOLBin execution with network connections and file creation events.
