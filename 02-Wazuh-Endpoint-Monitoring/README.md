# Wazuh Endpoint Monitoring and Threat Detection Lab

## Overview

This project demonstrates endpoint security monitoring and threat detection using Wazuh.

The objective of this lab was to simulate common attacker behaviors on a Linux endpoint and validate Wazuh's ability to detect, monitor, and investigate suspicious activities.

The project focuses on authentication monitoring, privilege escalation detection, file integrity monitoring, persistence detection, credential access monitoring, and root activity investigation.

---

## Lab Architecture

### Environment

| Component       | Purpose                                      |
| --------------- | -------------------------------------------- |
| Kali Linux      | Monitored endpoint                           |
| Wazuh Server    | Centralized monitoring and alerting platform |
| Wazuh Agent     | Endpoint telemetry collection                |
| Wazuh Dashboard | Security monitoring and investigation        |

---

## Project Objectives

* Deploy a functional Wazuh monitoring environment
* Generate endpoint security events
* Investigate suspicious activities
* Map events to MITRE ATT&CK
* Build detection and investigation workflows
* Develop SOC analyst skills

---

## Detection Scenarios

### Case 01 – Authentication Failures

Simulated multiple failed authentication attempts and investigated generated alerts.

**MITRE ATT&CK**

* T1110 – Brute Force

---

### Case 02 – Suspicious Sudo Activity

Simulated privilege escalation through sudo usage and monitored administrative actions.

**MITRE ATT&CK**

* T1548.003 – Sudo and Sudo Caching

---

### Case 03 – File Integrity Monitoring (Whodata)

Monitored file creation, modification, and deletion activities using Wazuh File Integrity Monitoring.

**MITRE ATT&CK**

* T1565.001 – Stored Data Manipulation
* T1070.004 – File Deletion

---

### Case 04 – Persistence via Cronjob

Simulated persistence by creating scheduled cron tasks on the monitored endpoint.

**MITRE ATT&CK**

* T1053.003 – Cron

---

### Case 05 – Sensitive File Access

Accessed Linux credential-related files to simulate post-exploitation credential gathering activity.

**MITRE ATT&CK**

* T1003.008 – OS Credential Dumping

---

### Case 06 – Root Privilege Activity

Executed privileged commands and investigated root-level administrative actions.

**MITRE ATT&CK**

* T1078 – Valid Accounts
* T1548.003 – Sudo and Sudo Caching

---

## Dashboard

A centralized Wazuh dashboard was created to visualize:

* Alert Timeline
* Alert Severity Distribution
* MITRE ATT&CK Coverage
* Authentication Activity
* File Integrity Monitoring Events
* Top Triggered Rules

---

## Skills Demonstrated

### Endpoint Monitoring

* Linux Security Monitoring
* Endpoint Visibility
* File Integrity Monitoring
* User Activity Monitoring

### Threat Detection

* Alert Analysis
* Detection Validation
* MITRE ATT&CK Mapping
* Threat Identification

### Incident Investigation

* Timeline Analysis
* Root Cause Investigation
* Alert Triage
* Security Reporting

### Wazuh Operations

* Agent Deployment
* Dashboard Creation
* Rule Analysis
* Security Event Investigation

---

## MITRE ATT&CK Coverage

| Technique | Description              |
| --------- | ------------------------ |
| T1110     | Brute Force              |
| T1548.003 | Sudo and Sudo Caching    |
| T1565.001 | Stored Data Manipulation |
| T1070.004 | File Deletion            |
| T1053.003 | Cron                     |
| T1003.008 | OS Credential Dumping    |
| T1078     | Valid Accounts           |

---

## Learning Outcomes

This project provided hands-on experience in:

* Endpoint Security Monitoring
* Threat Detection and Investigation
* Wazuh Administration
* Linux Security Analysis
* MITRE ATT&CK Mapping
* Security Dashboard Development

---

## Project Status

Completed

---
