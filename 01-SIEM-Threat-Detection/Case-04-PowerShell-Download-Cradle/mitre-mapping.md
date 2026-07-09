# MITRE ATT&CK Mapping

## Overview
This document maps the detected payload delivery and script runtime execution activity against the official enterprise MITRE ATT&CK matrix.

## Matrix Classifications

| Parameter | Technique 1 | Technique 2 |
| :--- | :--- | :--- |
| **Tactic** | Execution | Command and Control |
| **Technique Code** | [T1059.001 - PowerShell](https://attack.mitre.org/techniques/T1059/001/) | [T1105 - Ingress Tool Transfer](https://attack.mitre.org/techniques/T1105/) |
| **Description** | Used to trigger logic blocks and manipulate runtime tasks on the system. | Used to fetch tools and files from external server controls. |

## Telemetry Mapping Evidence
Our SIEM environment captured the behavior and verified execution across multiple vectors:
* **Sysmon Event ID 1 (Process Creation):** Documented the usage of `powershell.exe` handling script strings mapping out to an external server.
* **Sysmon Event ID 3 (Network Connection):** Verified the network transport handshake, binding the local process layer to the target attacker listener network socket.

---
*For holistic strategic mitigation, architectural guidelines, and sub-technique details, reference the links directly on the [MITRE ATT&CK T1059.001 Framework](https://attack.mitre.org/techniques/T1059/001/) and [MITRE ATT&CK T1105 Framework](https://attack.mitre.org/techniques/T1105/).*
