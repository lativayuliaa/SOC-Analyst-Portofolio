# Suspicious DNS Requests Analysis

## Overview

This case demonstrates how DNS traffic can be monitored and investigated using Wireshark and Suricata.

DNS is one of the most commonly abused protocols by attackers for command-and-control communication, domain resolution, malware updates, and infrastructure discovery.

The objective of this exercise was to generate DNS traffic, inspect DNS queries and responses, identify suspicious domain requests, and validate observations using packet-level analysis.

---

## Scenario

Several DNS queries were generated using standard lookup utilities.

Both legitimate and suspicious domain requests were performed to simulate normal user activity and potentially malicious DNS behavior.

---

## Lab Environment

Monitoring Host:

* Kali Linux
* Suricata IDS
* Wireshark

Traffic Sources:

* DNS Queries
* DNS Responses
* NXDOMAIN Responses

---

## Attack Simulation

DNS requests were generated using:

```bash
nslookup google.com

nslookup facebook.com

nslookup github.com
```

A suspicious domain lookup was also performed:

```bash
nslookup <suspicious-domain>
```

This generated DNS requests and responses that could be inspected and analyzed.

---

## Detection Sources

### Wireshark

Wireshark was used to capture and inspect DNS traffic.

Observed elements included:

* Query Names
* Response Records
* DNS Servers
* Returned IP Addresses
* NXDOMAIN Responses

### Suricata IDS

Suricata was used to observe DNS-related events and provide additional network visibility.

---

## Findings

The following indicators were identified:

* DNS queries and responses
* Queried domains
* DNS server communication
* Successful resolutions
* Failed resolutions (NXDOMAIN)

---

## Security Impact

Suspicious DNS activity may indicate:

* Malware communication
* Domain Generation Algorithms (DGA)
* Command and Control activity
* Data exfiltration attempts
* Infrastructure discovery

---

## Outcome

The DNS activity was successfully captured and analyzed.

Wireshark provided packet-level visibility into DNS communications, while Suricata supplied additional network monitoring capabilities.

---
