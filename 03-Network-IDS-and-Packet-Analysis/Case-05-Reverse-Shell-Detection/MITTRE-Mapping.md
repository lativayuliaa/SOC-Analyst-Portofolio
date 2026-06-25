# MITRE ATT&CK Mapping

## Technique

### T1059 - Command and Scripting Interpreter

Adversaries may use command-line interpreters and scripting environments to execute commands on compromised systems.

---

## Related Technique

### T1071 - Application Layer Protocol

Adversaries may use common network protocols to communicate with compromised systems.

---

## Tactic

### Execution

Commands were executed through an interactive shell session.

### Command and Control

The reverse shell established a communication channel between the compromised host and the attacker.

---

## Detection Evidence

Observed Indicators:

* Reverse shell connection
* Interactive command execution
* Persistent TCP session
* Outbound communication to attacker-controlled host

---

## Detection Sources

### Wireshark

* TCP Session Analysis
* Command Visibility
* Stream Reconstruction
* Packet Inspection

### Suricata IDS

* Network Monitoring
* Connection Visibility

---

## Security Relevance

Reverse shells are commonly observed during post-exploitation activities and provide attackers with direct access to compromised systems.

Monitoring unusual outbound connections can help identify command and control channels.

---

## ATT&CK Mapping Summary

| Technique ID | Technique                         |
| ------------ | --------------------------------- |
| T1059        | Command and Scripting Interpreter |
| T1071        | Application Layer Protocol        |

| Tactic              |
| ------------------- |
| Execution           |
| Command and Control |
