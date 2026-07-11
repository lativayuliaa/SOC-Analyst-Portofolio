# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Credential Access |
| **Technique ID Vector** | [T1110 - Brute Force](https://attack.mitre.org/techniques/T1110/) |
| **Observed Telemetry Footprint** | Concentrated authentication attempts over TCP Port 22, high connection frequency, consecutive failed password logs |

---

## 🧩 Threat Profile Description
Adversaries use brute-force tactics to systematically guess account credentials and gain unauthorized access to target host environments. By leveraging automated scripts and predefined dictionary files, threat actors run through vast lists of common passwords against services like SSH. If successful, this grants the attacker immediate terminal access, creating a launchpad for privilege escalation, local persistence establishment, or lateral network propagation.

---

## 📊 Detection Evidence Alignment
The telemetry gathered across the network and host sensors provides definitive evidence matching the enterprise matrix profile definitions:

* **Suricata IDS Telemetry:** Generates deterministic inline network security alerts by tracking the anomalous volume and speed of incoming SSH protocol handshakes.
* **Wireshark Packet Telemetry:** Documents the transport layer footprint, showing high-density TCP connection clusters targeting Port 22.
* **Linux Security Log Telemetry:** Confirms host-level impacts by recording explicit `Failed password` event blocks matching the attacker's source IP address.

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were collected and processed through the following structural layers:
* **Network-Based Collection:** Suricata NIDS Rule Manager & Wireshark Protocol Dissector.
* **Host-Based Collection:** Linux System Authentication Daemon Logs (`/var/log/auth.log`).
