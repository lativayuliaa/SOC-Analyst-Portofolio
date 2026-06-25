# Investigation Report

## Alert Summary

A file download event was generated and analyzed to simulate a potential payload delivery scenario.

The activity involved a client system downloading a file from a web server using the HTTP protocol.

---

## Investigation Steps

### Step 1 - Generate File Transfer Activity

A sample payload file was hosted on a web server and downloaded using wget.

This generated HTTP traffic suitable for network monitoring and packet analysis.

---

### Step 2 - Review HTTP Requests

Wireshark packet captures were analyzed.

Observed information included:

* HTTP GET Request
* Requested File Name
* Source IP Address
* Destination IP Address

---

### Step 3 - Review HTTP Responses

The server response was inspected.

Evidence confirmed:

* Successful HTTP Response
* File Transfer Completion
* Delivered Content

---

### Step 4 - Follow TCP Stream

TCP Stream analysis was performed to reconstruct the complete communication session.

The transferred file content was successfully observed within the session.

---

### Step 5 - Validate Monitoring Data

Suricata logs were reviewed to identify HTTP-related network events and validate observed activity.

---

## Risk Assessment

Suspicious file transfers may indicate:

* Malware Delivery
* Payload Distribution
* Tool Transfer
* Initial Access Support Activity

In this simulation, the transferred file was a benign test payload.

---

## Classification

Informational

---

## MITRE ATT&CK

* T1105 - Ingress Tool Transfer

---

## Evidence Sources

### Network Evidence

* Wireshark HTTP Analysis
* TCP Stream Reconstruction

### Monitoring Evidence

* Suricata HTTP Events

---

## Conclusion

The file transfer activity was successfully detected and investigated.

Wireshark provided detailed visibility into the HTTP transaction and transferred content, while Suricata supplied supporting network monitoring evidence.

The observed behavior is consistent with file transfer activity that could be associated with payload delivery techniques used by adversaries.
