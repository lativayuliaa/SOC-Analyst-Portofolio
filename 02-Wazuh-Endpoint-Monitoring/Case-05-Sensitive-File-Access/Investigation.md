# Investigation Report

## Alert Summary

Sensitive Linux credential files were accessed on the monitored endpoint.

The activity involved reading account information and password hash data from system credential files.

---

## Investigation Steps

### Step 1 - Review Activity

The observed commands accessed files commonly targeted during post-exploitation.

Files reviewed:

* /etc/passwd
* /etc/shadow

---

### Step 2 - Identify User

The responsible user account was identified from the available telemetry.

Information reviewed:

* Username
* Hostname
* Timestamp

---

### Step 3 - Analyze Intent

Access to credential files is commonly associated with:

* Credential harvesting
* Password hash collection
* Lateral movement preparation
* Privilege escalation preparation

---

### Step 4 - Determine Impact

The activity exposed credential-related information stored on the endpoint.

In a real-world environment, collected password hashes may later be used for:

* Offline password cracking
* Credential reuse attacks
* Privilege escalation attempts

---

## Classification

Suspicious

---

## MITRE ATT&CK

* T1003.008 - OS Credential Dumping: /etc/passwd and /etc/shadow

---

## Conclusion

Access to sensitive credential files was successfully observed during the simulation.

This activity represents a common post-exploitation technique used by attackers to gather credentials and expand access within an environment.
