# Case 03 - PowerShell Execution

## 📌 Objective

Detect and investigate PowerShell execution activity and parameter manipulation using Sysmon and the Elastic Stack.

---

## 💻 Lab Environment

| Machine | Role | IP Address |
| :--- | :--- | :--- |
| **Windows 10** | Victim (Execution Source) | `192.168.56.103` |
| **Host Laptop** | Elastic + Kibana (SIEM) | `192.168.56.1` |

---

## ⚔️ Attack Scenario & Commands Used

A user executed PowerShell commands on the Windows endpoint using parameters such as **`-nop`** (*NoProfile*) and **`-w hidden`** (*WindowStyle Hidden*). These options are commonly abused by adversaries to evade detection by disabling PowerShell profiles and hiding the PowerShell window from end users.

```powershell
powershell.exe -nop -c "Get-Process"
powershell.exe -nop -w hidden -c "Get-Date"
```

Sysmon captured the full command-line arguments, allowing analysts to identify the suspicious PowerShell execution and its associated parameters.

---

## 🔍 Detection & Key Findings

- **Detection Method:** Sysmon Event ID 1 (Process Creation) forwarded via Winlogbeat
- **Process Name:** `powershell.exe`
- **Parent Process:** `explorer.exe` (Executed directly from the Windows graphical interface)
- **Target User:** `vboxuser`
- **Hostname:** `WINDOWS10`
- **MITRE ATT&CK Mapping:**
  - `T1059.001` – PowerShell

---

## 📖 Case Documentation & References

For a detailed analysis of the collected telemetry, detection workflow, and MITRE ATT&CK mapping, refer to the supporting documentation below:

- 🕵️ **Investigation Report:** [investigation.md](investigation.md)
- 🛡️ **MITRE ATT&CK Mapping:** [mitre-mapping.md](mitre-mapping.md)
