# SOAR Workflow

## Workflow Overview

The SOAR workflow consists of five major stages.

---

## 1. Event Collection

Windows Security Events are collected from Elasticsearch using the n8n Elasticsearch node.

Examples:

- Event ID 4625
- Event ID 4720
- Event ID 4104

---

## 2. Risk Score Calculation

Each event is assigned a risk score according to predefined detection rules.

Example:

| Event | Risk Score |
|--------|-----------:|
| Failed Login | 40 |
| New User Created | 60 |
| Encoded PowerShell | 90 |
| Mimikatz | 100 |

---

## 3. Event Classification

The workflow separates events into two branches.

### Branch 1

Failed Login (4625)

↓

Brute Force Correlation

↓

Threshold Detection

---

### Branch 2

Risk Score

↓

High Risk Detection

---

## 4. Incident Creation

When a detection rule is triggered, n8n automatically creates a Jira Security Incident.

Incident information includes:

- Severity
- Hostname
- Username
- MITRE ATT&CK Technique
- Findings

---

## 5. Automated Response

After creating the Jira incident, an HTTP Request sends the detection information to a Python Flask API.

The API executes a PowerShell command that performs the configured response action.

Current implementation:

- Disable Local User (Proof of Concept)

---

## Workflow Summary

```
Elastic
   │
Risk Score
   │
Event Classification
   │
───────────────
│             │
Brute Force   High Risk
│             │
──────┬────────
      ▼
Create Jira
      ▼
Automated Response
```
