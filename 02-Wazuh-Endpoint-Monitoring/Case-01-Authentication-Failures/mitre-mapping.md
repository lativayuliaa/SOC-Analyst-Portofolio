# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Credential Access |
| **Technique ID Vector** | [T1110 - Brute Force](https://attack.mitre.org/techniques/T1110/) |
| **Observed Telemetry Footprint** | Sequential Password Validation Failures & PAM System Error Sequences |

---

## 🧩 Threat Profile Description
Adversaries frequently attempt to gain access to corporate networks or elevated user contexts by systematically guessing account combinations or executing brute-force dictionary attacks. By monitoring system authorization blocks (`auth.log`), security operators can block the initial enumeration phase before attackers transition into internal lateral movement stages.

---

## 📊 SIEM Framework Evidence Alignment
Wazuh features native visualization maps that dynamically categorize active host alerts against the industry-standard matrix taxonomy. The triggered authentication event parameters accurately populate the corresponding framework matrix blocks within the dashboard console:

![Wazuh MITRE ATT&CK Framework Mapping Dashboard](assets/ss-4-mitre-att%26ck.png)

## 🗃️ Telemetry Monitoring Source
The behavioral intelligence artifacts were successfully ingested and normalized using the following detection paths:
* **Log Pipeline Architecture:** Wazuh Agent log collection module.
* **Host Telemetry Points:** Linux PAM Engine Log Pipelines & Internal Security Authorization Repositories.
