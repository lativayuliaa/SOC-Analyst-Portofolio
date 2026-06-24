# MITRE ATT&CK Mapping

## Technique

### T1053.003 - Cron

Adversaries may use cron jobs to execute commands or scripts at scheduled intervals in order to maintain persistence on Linux systems.

---

## Tactic

### Persistence

The attacker attempts to maintain access to the compromised system across reboots and user sessions.

---

## Detection Evidence

Observed Indicators:

* Cron configuration modification
* Scheduled task creation
* File integrity alerts related to cron files

---

## Detection Source

* Wazuh File Integrity Monitoring (FIM)
* Whodata Monitoring
* Linux Cron Configuration Files
