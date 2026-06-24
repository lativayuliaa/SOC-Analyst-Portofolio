# Investigation Report

## Alert Summary

A network reconnaissance event was detected during monitoring activities.

Suricata generated alerts associated with Nmap scanning behavior, and packet captures were reviewed using Wireshark to validate the activity.

---

## Investigation Steps

### Step 1 - Review Alert

A Suricata alert indicated potential network scanning activity.

Information reviewed:

* Source IP
* Destination IP
* Timestamp
* Signature Name

---

### Step 2 - Validate Traffic

Wireshark packet captures were analyzed to verify the alert.

Observed behavior:

* Multiple TCP SYN packets
* Repeated connection attempts
* Port enumeration activity

---

### Step 3 - Identify Targeted Services

Packet analysis revealed that multiple ports were probed during the scan.

This behavior is consistent with service discovery and reconnaissance techniques.

---

### Step 4 - Assess Risk

Reconnaissance activity may indicate:

* Attack preparation
* Target profiling
* Service enumeration
* Vulnerability identification

No exploitation attempts were observed during this simulation.

---

## Classification

Suspicious

---

## MITRE ATT&CK

* T1046 - Network Service Discovery

---

## Evidence Sources

### Detection

* Suricata IDS Alert

### Validation

* Wireshark Packet Analysis

---

## Conclusion

The activity was confirmed as network reconnaissance conducted using Nmap.

Suricata successfully detected the scanning behavior, while Wireshark provided packet-level evidence supporting the investigation findings.
