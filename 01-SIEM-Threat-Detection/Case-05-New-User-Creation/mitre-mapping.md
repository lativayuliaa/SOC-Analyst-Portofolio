# MITRE ATT&CK Mapping

## Overview
This document maps the rogue local credential generation activity against the official enterprise MITRE ATT&CK matrix infrastructure.

## Matrix Classifications

| Matrix Category | Details |
| :--- | :--- |
| **Tactics** | Persistence, Privilege Escalation |
| **Technique Code** | [T1136.001 - Create Account: Local Account](https://attack.mitre.org/techniques/T1136/001/) |
| **Victim Target** | Windows 10 (`192.168.56.103`) |
| **Telemetry Vector** | Windows Security Logs (Event ID 4720) via Winlogbeat |

## Description
Adversaries may create local accounts to maintain persistent access to host systems if their primary access channels (like web shells, active implants, or stolen session cookies) are discovered and terminated. In certain conditions, creating an account with high privileges allows the actor to escalate their baseline execution context within the network cell.

## Observed Telemetry Evidence
Evidence processing was successfully logged inside our centralized Elastic SIEM platform through:
* **Windows Security Event ID 4720:** Documented the exact event attributes, identifying the actor account name alongside the newly minted credential baseline metadata.

---
*For a comprehensive matrix breakdown, architectural reference guidelines, and sub-technique details, browse the official [MITRE ATT&CK T1136.001 Reference Matrix](https://attack.mitre.org/techniques/T1136/001/).*
