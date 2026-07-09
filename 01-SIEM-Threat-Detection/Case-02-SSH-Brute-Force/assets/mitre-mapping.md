# MITRE ATT&CK Mapping

## Overview
This document maps the detected credential-guessing activity against the MITRE ATT&CK framework matrix to classify the adversary's tactics and techniques.

| Matrix Category | Details |
| :--- | :--- |
| **Tactic** | Credential Access |
| **Technique** | [T1110 - Brute Force](https://attack.mitre.org/techniques/T1110/) |
| **Adversary Source** | Kali Linux (`192.168.56.102`) |
| **Victim Target** | Windows 10 (`192.168.56.103`) |
| **Detection Telemetry** | Windows Security Logs (Event ID 4624 & 4625) via Elastic Stack |

## Description
The adversary attempted multiple SSH logins against the target host using an automated wordlist. After generating several failed authentication events, the valid password was identified, allowing the attacker to successfully gain unauthorized access to the system.

## Observed Telemetry Evidence
The execution of this specific technique was explicitly captured by our Elastic SIEM deployment via:
* **Event ID 4625 (Failed Logon):** Captured the automated guessing activity.
* **Event ID 4624 (Successful Logon):** Captured the post-brute-force compromise entry point.

---
*For more information regarding mitigation, detection strategies, and sub-techniques, refer to the official [MITRE ATT&CK T1110 Reference](https://attack.mitre.org/techniques/T1110/).*
