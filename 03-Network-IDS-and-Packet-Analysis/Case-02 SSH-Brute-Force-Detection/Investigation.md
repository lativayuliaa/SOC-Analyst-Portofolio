# Investigation Report

## Alert Summary

Suspicious SSH authentication activity was detected during monitoring operations.

The activity consisted of multiple login attempts originating from a single source host targeting an SSH service running on a Linux system.

---

## Investigation Steps

### Step 1 - Review Attack Activity

Hydra was used to perform repeated SSH authentication attempts against the target host.

The activity generated a high volume of login requests over TCP Port 22.

---

### Step 2 - Review Suricata Alerts

Suricata monitoring logs were reviewed to identify indicators associated with suspicious SSH activity.

Alert details included:

* Source IP Address
* Destination IP Address
* Timestamp
* Detection Signature

---

### Step 3 - Validate Network Traffic

Wireshark packet captures were analyzed to verify the attack behavior.

Observed indicators:

* Multiple TCP connections
* Repeated SSH sessions
* High connection frequency
* Communication over Port 22

---

### Step 4 - Review Host Evidence

Authentication logs on the target system were reviewed.

Evidence confirmed:

* Failed password attempts
* Repeated authentication failures
* User account targeting

---

### Step 5 - Risk Assessment

This activity is consistent with SSH brute force behavior.

Potential objectives include:

* Account compromise
* Unauthorized access
* Privilege escalation
* Persistence establishment

---

## Classification

Suspicious

---

## MITRE ATT&CK

* T1110 - Brute Force

---

## Evidence Sources

### Attack Evidence

* Hydra Output

### Detection Evidence

* Suricata IDS Alerts

### Network Evidence

* Wireshark Packet Analysis

### Host Evidence

* Linux Authentication Logs

---

## Conclusion

The activity was confirmed as an SSH brute force attack.

Multiple failed authentication attempts were observed and validated through network monitoring, packet analysis, and host-based evidence.

The attack successfully demonstrated credential access behavior consistent with MITRE ATT&CK Technique T1110 (Brute Force).
