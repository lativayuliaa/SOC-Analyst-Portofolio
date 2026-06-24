# Network IDS and Packet Analysis Lab Setup

## Overview

This lab was created to build a Network Intrusion Detection and Packet Analysis environment using Suricata and Wireshark.

The objective of the setup phase was to deploy a functional Network Intrusion Detection System (NIDS), configure detection rules, validate network visibility, and prepare the environment for attack simulations and packet-level investigations.

The lab combines signature-based detection with packet analysis techniques commonly used by Security Operations Center (SOC) analysts and Incident Responders.

---

## Lab Environment

| Component        | Purpose                                   |
| ---------------- | ----------------------------------------- |
| Kali Linux       | Attack simulation and monitoring host     |
| Suricata         | Network Intrusion Detection System (NIDS) |
| Wireshark        | Packet capture and traffic analysis       |
| Suricata Ruleset | Signature-based threat detection          |

---

## Project Objectives

* Deploy a Network Intrusion Detection System
* Configure and update Suricata detection rules
* Capture and analyze network traffic
* Validate IDS alerts using packet analysis
* Develop network security monitoring skills
* Perform threat detection and investigation

---

## Installation Process

### Verify Suricata Installation

The following command was used to verify the installed version:

```bash
suricata --build-info
```

---

### Identify Active Network Interface

The active network interface was identified using:

```bash
ip a
```

The selected interface was later used for packet inspection and traffic monitoring.

---

### Update Detection Rules

Suricata detection rules were updated using:

```bash
sudo suricata-update
```

This ensured the IDS operated with the latest available threat signatures.

---

### Start Suricata

Suricata was started on the monitored network interface:

```bash
sudo suricata -i <interface>
```

The IDS engine successfully initialized and began inspecting network traffic.

---

### Verify Wireshark Installation

Wireshark was used as the primary packet analysis platform.

The installation was verified using:

```bash
wireshark --version
```

Wireshark was later used to:

* Analyze captured packets
* Validate IDS alerts
* Identify network indicators
* Investigate suspicious traffic

---

## Validation

The following checks were successfully completed:

* Suricata installation verified
* Active network interface identified
* Detection rules updated
* IDS engine started successfully
* Packet inspection enabled
* Wireshark installation verified
* Packet capture functionality confirmed

---

## Skills Demonstrated

### Network Security Monitoring

* IDS Deployment
* Network Visibility
* Signature-Based Detection
* Traffic Monitoring

### Packet Analysis

* Packet Inspection
* Protocol Analysis
* Traffic Validation
* IOC Identification

### Linux Administration

* Service Management
* Interface Analysis
* Security Tool Deployment

---

## Outcome

The Network IDS and Packet Analysis environment was successfully deployed and validated.

The lab is now prepared for attack simulations and investigations including:

* Nmap Scan Detection
* SSH Brute Force Detection
* Suspicious DNS Activity
* File Download Detection
* Reverse Shell Detection
* Packet Investigation and IOC Extraction

---
