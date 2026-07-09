# Case 01 - Nmap Detection

## 📌 Objective

Detect and investigate network reconnaissance activity performed against a Windows 10 host using Nmap within the Elastic SIEM environment.

---

## 💻 Lab Environment

| Machine | Role | IP Address |
| :--- | :--- | :--- |
| **Kali Linux** | Attacker | `192.168.56.102` |
| **Windows 10** | Victim | `192.168.56.103` |
| **Host Laptop** | Elastic + Kibana (SIEM) | `192.168.56.1` |

---

## ⚔️ Attack Scenario & Commands Used

The attacker performed an aggressive **Nmap** scan against the Windows endpoint to identify open ports, detect the operating system, and enumerate running network services.

```bash
sudo nmap -A 192.168.56.103
```

The screenshot below shows the scan results generated from the attacker's machine.

![Nmap Scan](assets/ss-1-nmap-scan.png)

---

## 🔍 Detection & Key Findings

- **Detection Method:** Sysmon Event ID 3 (Network Connection) forwarded via Winlogbeat
- **Source IP (Attacker):** `192.168.56.102`
- **Destination IP (Victim):** `192.168.56.103`
- **Victim Hostname:** `WINDOWS10`
- **MITRE ATT&CK Mapping:**
  - `T1046` – Network Service Discovery

---

## 📖 Case Documentation & References

For a detailed analysis of the captured network telemetry, investigation workflow, and MITRE ATT&CK mapping, refer to the supporting documentation below:

- 🕵️ **Investigation Report:** [investigation.md](investigation.md)
- 🛡️ **MITRE ATT&CK Mapping:** [mitre-mapping.md](mitre-mapping.md)
