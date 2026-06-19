# Case 06 - LOLBins Abuse

## Objective

Detect and investigate the abuse of a Windows Living Off The Land Binary (LOLBin) using Sysmon and Elastic Stack.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

The built-in Windows utility `certutil.exe` was executed to calculate the SHA256 hash of a file. Adversaries commonly abuse LOLBins to evade detection and perform malicious actions while relying on trusted Windows binaries.

## Command Used

```cmd
certutil.exe -hashfile C:\Windows\System32\notepad.exe SHA256
```

## Detection Method

Sysmon Event ID 1 (Process Creation)

## Findings

* Process Name: certutil.exe
* Parent Process: cmd.exe
* User: vboxuser
* Hostname: WINDOWS10

## MITRE ATT&CK

* T1218 - System Binary Proxy Execution

## References

* Investigation/.md
* MITRE-Mapping.md
