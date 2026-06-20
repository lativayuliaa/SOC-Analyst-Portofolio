# SIEM Threat Detection and Monitoring Lab

## Overview

This project demonstrates the implementation of a Security Information and Event Management (SIEM) environment using Elastic Stack, Sysmon, and Winlogbeat.

The objective of this lab is to simulate real-world attack scenarios and investigate them through log analysis, detection engineering, MITRE ATT&CK mapping, and incident investigation workflows.

---

## Lab Architecture

* Host Machine

  * Elastic Stack
  * Kibana

* Windows 10 VM

  * Sysmon
  * Winlogbeat

* Kali Linux VM

  * Attack Simulation

---

## Technologies Used

* Elastic Stack
* Kibana
* Sysmon
* Winlogbeat
* Kali Linux
* Windows 10
* VirtualBox

---

## Attack Scenarios

| Case    | Scenario                   | MITRE ATT&CK |
| ------- | -------------------------- | ------------ |
| Case 01 | Network Service Discovery  | T1046        |
| Case 02 | SSH Brute Force            | T1110        |
| Case 03 | PowerShell Execution       | T1059.001    |
| Case 04 | PowerShell Download Cradle | T1105        |
| Case 05 | New User Creation          | T1136.001    |
| Case 06 | LOLBins Abuse              | T1218        |
| Case 07 | Encoded PowerShell         | T1059.001    |
| Case 08 | Certutil Payload Download  | T1218, T1105 |
| Case 09 | Windows Service Creation   | T1543.003    |

---

## Dashboard

### SOC Overview Dashboard

Provides a high-level overview of security events, process activity, authentication failures, service installations, and MITRE ATT&CK coverage.

### PowerShell Threat Hunting Dashboard

Monitors PowerShell execution and identifies encoded commands and suspicious parent-child process relationships.

### LOLBins Monitoring Dashboard

Tracks the abuse of built-in Windows utilities such as PowerShell, Certutil, and Command Prompt.

### Brute Force Investigation Dashboard

Analyzes authentication failures, successful logins, source IP addresses, and targeted accounts.

---

## MITRE ATT&CK Coverage

### Reconnaissance

* T1046 - Network Service Discovery

### Credential Access

* T1110 - Brute Force

### Execution

* T1059.001 - PowerShell

### Persistence

* T1136.001 - Create Account
* T1543.003 - Windows Service

### Defense Evasion

* T1218 - System Binary Proxy Execution

### Command and Control

* T1105 - Ingress Tool Transfer

---

## Skills Demonstrated

* SIEM Administration
* Log Analysis
* Detection Engineering
* Threat Hunting
* MITRE ATT&CK Mapping
* Sysmon Analysis
* Windows Event Analysis
* Incident Investigation
* Dashboard Development
* Security Monitoring

---


---

## Author

Built as part of a Blue Team and SOC Analyst portfolio project focusing on detection engineering, threat hunting, and incident investigation using Elastic Stack.
