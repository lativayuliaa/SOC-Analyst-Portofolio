# MITRE ATT&CK Mapping

## Overview
This document maps the detected reconnaissance activity against the MITRE ATT&CK framework matrix to classify the adversary's tactics and techniques.

| Matrix Category | Details |
| :--- | :--- |
| **Tactic** | Discovery |
| **Technique** | [T1046 - Network Service Discovery](https://attack.mitre.org/techniques/T1046/) |
| **Adversary Source** | Kali Linux (`192.168.56.102`) |
| **Victim Target** | Windows 10 (`192.168.56.103`) |
| **Detection Telemetry** | Sysmon (Event ID 3) via Elastic Stack |

## Description
The adversary utilized the Nmap network utility to enumerate active services exposed by the target host. Network service discovery is commonly leveraged during the discovery phase to map out the network footprint, identify open ports, and fingerprint running services for downstream exploitation planning.

## Observed Telemetry Evidence
The execution of this specific technique was explicitly captured by our Elastic SIEM deployment via:
* **Sysmon Event ID 3 (Network Connection):** Multiple connection attempts directed at various ports on the victim machine from the attacker's IP, providing the necessary telemetry data to confirm scanning activity.

---
*For more information regarding mitigation, detection strategies, and sub-techniques, refer to the official [MITRE ATT&CK T1046 Reference](https://attack.mitre.org/techniques/T1046/).*
