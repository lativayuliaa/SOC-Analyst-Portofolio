# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Command and Control |
| **Technique ID Vector** | [T1105 - Ingress Tool Transfer](https://attack.mitre.org/techniques/T1105/) |
| **Observed Telemetry Footprint** | Explicit HTTP GET requests, plaintext TCP stream content strings, web server application event records |

---

## 🧩 Threat Profile Description
Adversaries frequently move tools, scripts, exploit kits, and second-stage malware payloads from external infrastructure into an endangered environment to advance their operational objectives. Ingress tool transfers typically occur after initial access has been established, allowing attackers to customize their toolkit based on the specific defenses and configuration of the compromised endpoint.

Monitoring raw web transfer methodologies provides defenders with a critical chokepoint to detect staging operations before post-exploitation tools can execute.

---

## 📊 Detection Evidence Alignment
The telemetry artifacts logged during this scenario align with standard enterprise matrix framework detection models:

* **HTTP Traffic Verification:** Wireshark isolates the explicit download requests, tracking file extensions and host endpoints directly out of cleartext transport segments.
* **TCP Session Reassembly:** Reconstructing raw TCP sessions allows defenders to review the file content over the wire, providing input for signature matching or threat-hunting reviews.
* **Application Layer Alert Logs:** Suricata extracts protocol metadata to maintain clean visibility into web communication events across non-standard port ranges.

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were collected and processed through the following structural layers:
* **Network Forensic Core:** Wireshark Deep Packet Dissector Subsystem (TCP Stream Assembler).
* **Network Inspection Core:** Suricata Engine NIDS HTTP Log Extraction Framework.
