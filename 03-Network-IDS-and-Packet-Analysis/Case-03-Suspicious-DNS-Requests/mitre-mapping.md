# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Command and Control |
| **Technique ID Vector** | [T1071.004 - Application Layer Protocol: DNS](https://attack.mitre.org/techniques/T1071/004/) |
| **Observed Telemetry Footprint** | Explicit application lookup strings, standard transaction tracking logs, resolution returns, and NXDOMAIN error records |

---

## 🧩 Threat Profile Description
Adversaries frequently leverage the Domain Name System (DNS) to establish robust, persistent communication paths out of compromised networks. Because firewalls almost universally permit Port 53 outbound queries to maintain baseline operational resolution, DNS serves as an optimal infrastructure layer for stealthy command execution, initial target discovery validation, and data exfiltration. 

By hiding tiny chunks of encoded payloads within subdomains or TXT records, attackers can establish interactive shells or update command loops while evading legacy traffic analysis systems.

---

## 📊 Detection Evidence Alignment
The telemetry gathered across the network inspection architecture provides data matching the enterprise matrix profile definitions:

* **Wireshark Frame Dissection:** Isolates individual transaction strings, queries, and answer fields directly out of raw UDP/TCP streams on the wire.
* **Suricata Event Monitoring:** Provides comprehensive metadata extraction by capturing all internal domain lookup activities into structured, queryable network security logs.

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were collected and processed through the following structural layers:
* **Network Analysis Stack:** Wireshark Deep Packet Dissector Subsystem.
* **Application Visibility Stack:** Suricata Engine NIDS Protocol Logging Module.
