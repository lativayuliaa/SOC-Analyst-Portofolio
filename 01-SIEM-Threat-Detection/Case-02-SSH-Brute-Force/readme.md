# Case 02 - SSH Brute Force Detection

## 📌 Objective

Detect and investigate SSH brute-force activity targeting a Windows 10 host using the Elastic Stack and Windows Security Event Logs.

---

## 💻 Lab Environment

| Machine | Role | IP Address |
| :--- | :--- | :--- |
| **Kali Linux** | Attacker | `192.168.56.102` |
| **Windows 10** | Victim | `192.168.56.103` |
| **Host Laptop** | Elastic + Kibana (SIEM) | `192.168.56.1` |

---

## ⚔️ Attack Scenario & Commands Used

The attacker performed an automated SSH brute-force attack against the Windows endpoint using **Hydra**. The tool attempted multiple password combinations from a wordlist until valid credentials were identified.

```bash
hydra -l vboxuser -P pass.txt ssh://192.168.56.103
```

The screenshot below shows Hydra successfully discovering the target account's password.

![Hydra Success](assets/ss-1-hydra-success.png)

After obtaining valid credentials, the attacker established a remote interactive SSH session with the victim machine.

---

## 🔍 Detection & Key Findings

- **Detection Method:** Windows Security Event Logs collected via Winlogbeat
- **Observed Events:**
  - Event ID **4625** – Failed Logon
  - Event ID **4624** – Successful Logon
- **Source IP (Attacker):** `192.168.56.102`
- **Destination IP (Victim):** `192.168.56.103`
- **Target User:** `vboxuser`
- **Victim Hostname:** `WINDOWS10`
- **MITRE ATT&CK Mapping:**
  - `T1110` – Brute Force

---

## 📖 Case Documentation & References

For a detailed analysis of the authentication events, investigation workflow, and MITRE ATT&CK mapping, refer to the supporting documentation below:

- 🕵️ **Investigation Report:** [investigation.md](investigation.md)
- 🛡️ **MITRE ATT&CK Mapping:** [mitre-mapping.md](mitre-mapping.md)
