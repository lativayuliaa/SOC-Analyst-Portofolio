# Nmap Scan Detection

## Overview

This case demonstrates how Suricata and Wireshark can be used together to detect and investigate network reconnaissance activity.

Network scanning is commonly performed during the reconnaissance phase of an attack to identify open ports, running services, and potential attack vectors.

The objective of this exercise was to generate Nmap scanning traffic, detect it using Suricata IDS, and validate the activity through packet analysis in Wireshark.

---

## Scenario

An Nmap TCP SYN scan was performed against a target system.

Suricata monitored the network traffic and generated alerts associated with reconnaissance activity. Wireshark was then used to inspect the captured packets and validate the detected behavior.

---

## Attack Simulation

The following command was executed:

```bash
nmap -sS <target-ip>
```

The scan generated multiple TCP SYN packets to enumerate available services on the target host.

---

## Detection Method

### Suricata IDS

Suricata analyzed network traffic and generated alerts when reconnaissance signatures were detected.

### Wireshark Analysis

Wireshark was used to inspect packet-level evidence and verify the scanning behavior observed by Suricata.

---

## Findings

The following information was successfully identified:

* Source IP Address
* Destination IP Address
* Scanned Ports
* TCP SYN Packets
* Alert Signature
* Timestamp

---

## Security Impact

Network scanning may indicate:

* Reconnaissance activity
* Service enumeration
* Attack surface discovery
* Preparation for exploitation

---

## Outcome

The objective was successfully completed.

Suricata detected reconnaissance activity while Wireshark provided packet-level validation of the generated network traffic.

---
