# SSH Brute Force Detection

## Overview

This case demonstrates the detection and investigation of an SSH brute force attack using Suricata, Wireshark, and Linux authentication logs.

Brute force attacks are commonly used by attackers to gain unauthorized access by repeatedly attempting different password combinations against a target service.

The objective of this exercise was to simulate an SSH brute force attack, observe the generated network traffic, validate detection capabilities, and investigate the activity using multiple evidence sources.

---

## Scenario

A brute force attack was launched from Kali Linux (Attacker) against a target Linux system running an SSH service.

Hydra was used to automate authentication attempts using a predefined password list.

---

## Lab Topology

Attacker:

* Kali Linux
* Hydra
* Suricata IDS
* Wireshark

Target:

* Kali Linux
* OpenSSH Server

---

## Attack Simulation

The following command was executed:

```bash
hydra -l kali -P passwords.txt ssh://<target-ip>
```

Hydra generated multiple SSH authentication attempts against the target host.

---

## Detection Sources

### Suricata IDS

Suricata monitored network traffic and generated alerts associated with suspicious SSH activity.

### Wireshark

Wireshark was used to inspect packet-level evidence and validate repeated SSH connection attempts.

### Linux Authentication Logs

Authentication logs were reviewed to identify failed login attempts generated during the attack.

---

## Findings

The following indicators were observed:

* Multiple failed login attempts
* Repeated SSH connections
* Authentication failures
* SSH traffic over TCP Port 22
* Source and destination IP addresses

---

## Security Impact

SSH brute force attacks may lead to:

* Unauthorized access
* Credential compromise
* Privilege escalation
* Lateral movement

---

## Outcome

The brute force activity was successfully generated and investigated.

Suricata detected suspicious network activity, Wireshark validated packet-level behavior, and Linux authentication logs confirmed repeated failed login attempts.

---
