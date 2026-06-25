# Suspicious File Download Detection

## Overview

This case demonstrates how network monitoring and packet analysis can be used to identify and investigate file download activity.

File downloads are frequently observed during cyber attacks when adversaries transfer tools, malware payloads, scripts, or additional resources to compromised systems.

The objective of this exercise was to simulate a file transfer using HTTP, monitor the activity using Suricata, and analyze the network traffic using Wireshark.

---

## Scenario

A web server was created on a Linux target system to host a sample payload file.

The monitoring host downloaded the file using wget, generating HTTP traffic that could be inspected and analyzed.

---

## Lab Environment

Monitoring Host:

* Kali Linux
* Suricata IDS
* Wireshark

Target Host:

* Kali Linux
* Python HTTP Server

---

## Attack Simulation

A sample payload file was created:

```bash
echo "malware simulation" > payload.txt
```

A web server was started:

```bash
python3 -m http.server 8080
```

The file was downloaded from the monitoring host:

```bash
wget http://<target-ip>:8080/payload.txt
```

---

## Detection Sources

### Wireshark

Wireshark was used to inspect HTTP communications and file transfer activity.

Observed information included:

* HTTP Requests
* HTTP Responses
* File Names
* Server Information
* Download Content

### Suricata IDS

Suricata was used to observe HTTP-related events and provide additional network visibility.

---

## Findings

The following indicators were identified:

* HTTP GET Request
* Downloaded File Name
* Source IP Address
* Destination IP Address
* Successful HTTP Response
* File Transfer Content

---

## Security Impact

Suspicious file downloads may indicate:

* Malware delivery
* Tool transfer
* Payload staging
* Command and Control activity

---

## Outcome

The file transfer activity was successfully generated and analyzed.

Wireshark provided detailed packet-level visibility into the HTTP transaction, while Suricata supplied additional monitoring and event data.

---
