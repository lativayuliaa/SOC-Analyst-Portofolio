# MITRE ATT&CK Mapping

## Overview
This document maps the obfuscated shell script execution activity against the official enterprise MITRE ATT&CK framework baseline matrix category.

## Matrix Classifications

| Parameter | Tactic 1 | Tactic 2 |
| :--- | :--- | :--- |
| **Tactic Type** | Execution | Defense Evasion |
| **Technique Code** | [T1059.001 - PowerShell](https://attack.mitre.org/techniques/T1059/001/) | [T1059.001 - PowerShell](https://attack.mitre.org/techniques/T1059/001/) |
| **Operational Impact** | Triggering system commands and tasks. | Concealing raw execution strings from string analytics. |

## Description
Adversaries frequently apply standard Base64 string encoding structures to mask explicit operational activities from detection products. This structural camouflage allows code blocks to run directly within legitimate signed binary environments while keeping the internal payload parameters obscured from regular network filters and event inspection points.

## Observed Telemetry Evidence
Process behavior trace vectors were successfully collected and logged inside our central Elastic SIEM platform through:
* **Sysmon Event ID 1 (Process Creation):** Documented the process hierarchy tree, execution parameters, active user context, and system identification tags.

---
*For holistic strategic mitigation rules, architecture monitoring guidelines, and technical updates, check out the official [MITRE ATT&CK T1059.001 Reference Manual](https://attack.mitre.org/techniques/T1059/001/).*
