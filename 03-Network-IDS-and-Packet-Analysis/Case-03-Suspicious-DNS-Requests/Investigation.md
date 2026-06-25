# Investigation Report

## Alert Summary

DNS activity was observed and analyzed to identify potentially suspicious communication patterns.

Both legitimate and suspicious domain lookups were reviewed during the investigation.

---

## Investigation Steps

### Step 1 - Generate DNS Traffic

Multiple DNS queries were executed to generate network activity.

Queries included:

* Legitimate domains
* Suspicious domains
* Invalid domains

---

### Step 2 - Review DNS Traffic

Wireshark packet captures were analyzed using DNS filters.

Observed information:

* Source IP Address
* Destination DNS Server
* Query Names
* Response Codes
* Resolved IP Addresses

---

### Step 3 - Review DNS Responses

The DNS responses were analyzed to determine whether:

* The domain resolved successfully
* The request returned NXDOMAIN
* The response appeared normal

---

### Step 4 - Validate Network Activity

Suricata logs were reviewed to identify DNS-related events and confirm network visibility.

---

### Step 5 - Risk Assessment

Suspicious DNS behavior may indicate:

* Command and Control Communication
* Malware Beaconing
* Domain Generation Algorithms
* Data Exfiltration

No confirmed malicious communication was observed during this simulation.

---

## Classification

Informational

---

## MITRE ATT&CK

* T1071.004 - Application Layer Protocol: DNS

---

## Evidence Sources

### Network Evidence

* Wireshark DNS Analysis

### Monitoring Evidence

* Suricata DNS Events

---

## Conclusion

DNS activity was successfully captured and analyzed.

The investigation demonstrated how DNS traffic can be inspected, validated, and assessed for suspicious indicators using packet analysis and network monitoring tools.

The observed behavior was consistent with normal DNS resolution activity, including successful responses and NXDOMAIN results for invalid domains.
