# SOAR Automation using Elastic, n8n, Jira & Python

## Overview

This project demonstrates a Security Orchestration, Automation and Response (SOAR) workflow built using Elastic Stack, n8n, Jira, and Python.

The workflow automatically collects Windows Security Events from Elasticsearch, calculates a risk score, detects brute force attacks through event correlation, creates security incidents in Jira, and executes automated response actions.

This repository focuses on the workflow implementation and automation process rather than the source code.

---

## Technologies

- Elastic Stack
- Windows Event Logs
- Sysmon
- n8n
- Jira
- Python Flask
- PowerShell

---

## Workflow

```
Windows Security Events
          │
          ▼
 Elasticsearch
          │
          ▼
 Risk Score Calculation
          │
          ▼
 Event Classification
      ┌───────────────┐
      │               │
Brute Force      High Risk Event
Correlation            │
      │                │
      └──────┬─────────┘
             ▼
    Create Jira Incident
             ▼
 Execute Automated Response
```

---

## Detection Logic

### High Risk Detection

The workflow calculates a risk score for every incoming Windows security event.

Events with a risk score greater than or equal to **60** are considered security incidents and automatically generate a Jira ticket.

---

### SSH Brute Force Detection

Brute force attacks are detected by correlating multiple Windows Event ID **4625** (Failed Login) events.

If five or more failed login attempts are detected within a short period, the workflow automatically creates a security incident.

---

## Automated Response

Depending on the detected attack, the workflow performs automated response actions.

Current implementation includes:

- Create Jira Security Incident
- Disable suspicious local user account (Proof of Concept)

Future improvements:

- Firewall IP Blocking
- Host Isolation
- Email / Slack Notification
- Active Directory Integration

---

## Project Status

Completed

Current Features

- Windows Event Monitoring
- Risk Score Engine
- Brute Force Correlation
- Jira Integration
- Automated Response

---

## Author

Lativa Yulia Taviani
