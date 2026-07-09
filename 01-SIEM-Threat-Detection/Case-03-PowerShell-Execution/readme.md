# Case 03 - PowerShell Execution

## 📌 Objective
Detect and investigate PowerShell execution activity and parameter manipulation using Sysmon and the Elastic Stack.

## 💻 Lab Environment

| Machine | Role | IP Address |
| :--- | :--- | :--- |
| **Windows 10** | Victim (Execution Source) | `192.168.56.103` |
| **Host Laptop** | Elastic + Kibana (SIEM) | `192.168.56.1` |

---

## ⚔️ Attack Scenario & Commands Used
A user executed PowerShell commands on the Windows target host utilizing specific flags (`-nop` / NoProfile and `-w hidden` / WindowStyle Hidden) commonly leveraged by adversaries to bypass execution policies and hide windows from end-users.

```powershell
powershell.exe -nop -c "Get-Process"
powershell.exe -nop -w hidden -c "Get-Date"
```
