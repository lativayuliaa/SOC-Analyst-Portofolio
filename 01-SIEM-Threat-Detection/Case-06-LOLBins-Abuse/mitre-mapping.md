# MITRE ATT&CK Mapping

## Overview
This document maps the trusted native operating system utility abuse against the structured enterprise MITRE ATT&CK matrix classifications.

## Matrix Classifications

| Matrix Category | Details |
| :--- | :--- |
| **Tactic** | Defense Evasion |
| **Technique Code** | [T1218 - System Binary Proxy Execution](https://attack.mitre.org/techniques/T1218/) |
| **Target Host** | Windows 10 (`192.168.56.103`) |
| **Telemetry Pipeline** | Sysmon (Event ID 1 - Process Creation) via Winlogbeat |

## Description
Adversaries often abuse legitimate system binaries to proxy the execution of malicious commands or code blocks. By routing tasks through native utilities already signed and trusted by the root operating system, malicious operations can bypass administrative security boundaries, application whitelisting solutions, and strict execution logging controls.

## Observed Telemetry Evidence
Behavioral tracing parameters were validated inside our Elastic SIEM workspace via:
* **Sysmon Event ID 1 (Process Creation):** Documented the parent spawning tree, hash strings, and baseline execution user details.

---
*For in-depth mitigation guidelines, detection engineering principles, and a complete sub-technique list, inspect the [MITRE ATT&CK T1218 Reference Matrix](https://attack.mitre.org/techniques/T1218/).*
