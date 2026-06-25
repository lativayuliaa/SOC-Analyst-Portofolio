# Investigation Report

## Alert Summary

A reverse shell session was established between two Linux systems.

The target host initiated an outbound connection to an attacker-controlled listener, resulting in an interactive remote shell session.

---

## Investigation Steps

### Step 1 - Review Connection Establishment

A Netcat listener was started on the monitoring host.

The target system subsequently initiated a connection to the listener using a Bash reverse shell.

---

### Step 2 - Review Network Traffic

Wireshark packet captures were analyzed to identify communication between the two hosts.

Observed information included:

* Source IP Address
* Destination IP Address
* TCP Port 4444
* Session Duration

---

### Step 3 - Validate Interactive Activity

The session was reviewed using TCP Stream analysis.

Evidence confirmed:

* Interactive shell communication
* Command execution
* Bidirectional data transfer

---

### Step 4 - Review Session Contents

Commands executed during the session included:

* whoami
* hostname
* pwd
* id

These commands demonstrated successful remote command execution.

---

### Step 5 - Validate Monitoring Data

Suricata logs were reviewed to identify network events associated with the connection.

Monitoring data confirmed communication between the two hosts during the simulation.

---

## Risk Assessment

Reverse shell activity may indicate:

* System compromise
* Command and Control activity
* Post-exploitation operations
* Unauthorized remote access

This behavior should be considered highly suspicious in a production environment.

---

## Classification

High Severity

---

## MITRE ATT&CK

* T1059 - Command and Scripting Interpreter
* T1071 - Application Layer Protocol

---

## Evidence Sources

### Network Evidence

* Wireshark Traffic Analysis
* TCP Stream Reconstruction

### Monitoring Evidence

* Suricata Network Events

### Attack Evidence

* Netcat Listener
* Reverse Shell Session

---

## Conclusion

The activity was confirmed as a reverse shell session initiated from the target host.

Packet analysis revealed an interactive command channel that allowed remote command execution through a persistent TCP connection.

The observed behavior is consistent with post-exploitation activity commonly used by attackers to maintain remote access to compromised systems.
