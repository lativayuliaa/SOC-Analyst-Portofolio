# MITRE ATT&CK Mapping

## Technique 1

T1059.001 - PowerShell

### Tactic

Execution

### Description

PowerShell was used to execute commands on the victim system and retrieve a file from a remote host.

---

## Technique 2

T1105 - Ingress Tool Transfer

### Tactic

Command and Control

### Description

The victim machine downloaded a file from an external host controlled by the attacker.

---

## Attack Source

Kali Linux (192.168.56.102)

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Sysmon Event ID 1 - Process Creation
* Sysmon Event ID 3 - Network Connection

## Detection Method

Elastic Stack and Sysmon telemetry

## ATT&CK References

https://attack.mitre.org/techniques/T1059/001/

https://attack.mitre.org/techniques/T1105/
