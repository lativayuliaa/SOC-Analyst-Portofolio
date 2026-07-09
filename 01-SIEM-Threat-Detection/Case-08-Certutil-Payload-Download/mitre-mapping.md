# MITRE ATT&CK Mapping

## Overview
This document maps the trusted native utility ingress file delivery activity against the official enterprise MITRE ATT&CK framework baseline matrix category.

## Matrix Classifications

| Parameter | Technique 1 | Technique 2 |
| :--- | :--- | :--- |
| **Tactic Category** | Defense Evasion | Command and Control |
| **Technique Code** | [T1218 - System Binary Proxy Execution](https://attack.mitre.org/techniques/T1218/) | [T1105 - Ingress Tool Transfer](https://attack.mitre.org/techniques/T1105/) |
| **Operational Impact** | Routing commands through legitimate signed binaries to bypass application controls. | Transferring malicious utilities or files into compromised internal host cells. |

## Description
Adversaries often leverage native system binaries to download external files to circumvent static boundary configurations. Since default configurations often permit administrative tools to speak out onto networks, leveraging these assets allows threat groups to bring secondary execution vectors onto the client disk undetected by generic signature engines.

## Observed Telemetry Evidence
Behavior trace vectors were successfully collected and correlated inside our centralized Elastic SIEM workspace via:
* **Sysmon Event ID 1 (Process Creation):** Documented the process hierarchy tree, execution parameters, active user context, and system identification tags.
* **Sysmon Event ID 3 (Network Connection):** Bound the local client binary to the remote web server socket infrastructure.

---
*For holistic strategic mitigation rules, architecture monitoring guidelines, and technical updates, check out the official [MITRE ATT&CK T1218 Reference Manual](https://attack.mitre.org/techniques/T1218/) and [MITRE ATT&CK T1105 Reference Manual](https://attack.mitre.org/techniques/T1105/).*
