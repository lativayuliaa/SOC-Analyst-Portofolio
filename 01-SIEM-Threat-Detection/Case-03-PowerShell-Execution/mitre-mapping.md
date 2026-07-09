# MITRE ATT&CK Mapping

## Overview
This document maps the detected PowerShell utility execution activity against the official MITRE ATT&CK enterprise matrix infrastructure.

| Matrix Category | Details |
| :--- | :--- |
| **Tactic** | Execution |
| **Technique** | [T1059.001 - PowerShell](https://attack.mitre.org/techniques/T1059/001/) |
| **Victim Target** | Windows 10 (`192.168.56.103`) |
| **Telemetry Vector** | Sysmon (Event ID 1 - Process Creation) via Winlogbeat |

## Description
Adversaries frequently leverage PowerShell to deploy payloads, execute commands, and run malicious scripts directly in-memory to bypass traditional file-based signature discovery. This specific test observed command string injection aimed at system reconnaissance mapping (`Get-Process`).

## Observed Telemetry Evidence
Evidence processing was successfully analyzed inside our Elastic SIEM platform through:
* **Sysmon Event ID 1:** Documented the execution context, verification of the runtime process tree hashes, and command-line parameters used.

---
*For a comprehensive lookup of mitigations and administrative execution matrices, check out the official [MITRE ATT&CK T1059.001 Reference](https://attack.mitre.org/techniques/T1059/001/).*
