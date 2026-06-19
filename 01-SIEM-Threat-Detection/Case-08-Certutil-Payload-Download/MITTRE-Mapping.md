# MITRE ATT&CK Mapping

## Technique 1

T1218 - System Binary Proxy Execution

### Tactic

Defense Evasion

### Description

Adversaries may abuse trusted Windows binaries to execute commands and evade security controls.

---

## Technique 2

T1105 - Ingress Tool Transfer

### Tactic

Command and Control

### Description

Adversaries may transfer tools or payloads from an external host to a compromised system.

---

## Victim Host

Windows 10 (192.168.56.103)

## Attack Source

Kali Linux (192.168.56.102)

## Observed Events

* Sysmon Event ID 1 - Process Creation
* Sysmon Event ID 3 - Network Connection

## Detection Method

Elastic Stack and Sysmon telemetry

## ATT&CK References

https://attack.mitre.org/techniques/T1218/

https://attack.mitre.org/techniques/T1105/
