# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Classes** | Execution / Command and Control |
| **Technique ID Vectors** | [T1059 - Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059/) <br> [T1071 - Application Layer Protocol](https://attack.mitre.org/techniques/T1071/) |
| **Observed Telemetry Footprint** | Outbound non-standard destination port routing, persistent unencrypted TCP streaming, interactive terminal command execution strings |

---

## 🧩 Threat Profile Description
Adversaries leverage command and scripting interpreters to run code, launch administrative processes, and control host interfaces within compromised targets. By attaching these terminal environments to outbound network sockets, attackers form functional interactive reverse shells. 

This establishes a stealthy command-and-control connection that utilizes permitted outbound transport paths to bypass standard perimeter defenses. This persistent shell access enables a range of post-exploitation activities, including local network profiling, account privilege escalation, and tool orchestration.

---

## 📊 Detection Evidence Alignment
The behavioral threat artifacts captured across the monitoring stack align with standard enterprise matrix framework detection models:

* **TCP Stream Reconstruction:** Wireshark reassembles raw network streams to expose cleartext command interactions (`whoami`, `id`), providing high-fidelity evidence of terminal compromise.
* **Network Flow Logging:** Suricata captures metadata for outbound network connections across non-standard port arrays, maintaining precise session timelines and tracing communication paths between endpoints.

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were collected and processed through the following structural layers:
* **Network Reconstruction Layer:** Wireshark Forensic Packet Assembly Module.
* **Network Visibility Layer:** Suricata Engine Passive Flow Event Logging Subsystem.
