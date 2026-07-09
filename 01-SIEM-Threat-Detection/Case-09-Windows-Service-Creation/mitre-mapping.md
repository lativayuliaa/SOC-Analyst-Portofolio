# MITRE ATT&CK Mapping

## Overview
This document maps the unauthorized background Windows service creation activity against the official enterprise MITRE ATT&CK matrix.

## Matrix Classifications

| Parameter | Tactic 1 | Tactic 2 |
| :--- | :--- | :--- |
| **Tactic Type** | Persistence | Privilege Escalation |
| **Technique Code** | [T1543.003 - Windows Service](https://attack.mitre.org/techniques/T1543/003/) | [T1543.003 - Windows Service](https://attack.mitre.org/techniques/T1543/003/) |
| **Description** | Maintaining an enduring presence on the endpoint host. | Executing automated tasks under elevated system contexts. |

## Description
Adversaries may create or modify Windows services to execute malicious code blocks automatically on a persistent schedule. When a service is generated, it can be assigned to run under high-level administrative contexts (such as `NT AUTHORITY\SYSTEM`), allowing a threat actor to successfully transition a low-privilege foothold into a dominant system administrative position.

## Observed Telemetry Evidence
Process and configuration management logs were validated inside our central Elastic SIEM platform through:
* **Windows System Event ID 7045:** Captured the service registry event, pinpointing the service names, image file paths, and startup definitions.

---
*For a granular breakdown, architectural mitigation models, and standard sub-technique definitions, browse the official [MITRE ATT&CK T1543.003 Reference Matrix](https://attack.mitre.org/techniques/T1543/003/).*
