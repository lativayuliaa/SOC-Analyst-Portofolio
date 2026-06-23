# Wazuh Lab Setup

## Overview

This lab was built to simulate a real-world endpoint monitoring environment using Wazuh.

The objective is to monitor Linux endpoint activity, collect security events, and investigate suspicious behavior through Wazuh dashboards, alerts, and MITRE ATT&CK mappings.

---

## Lab Architecture

```text
+-----------------------+
|     Wazuh Server      |
|                       |
|  - Wazuh Manager      |
|  - Wazuh Dashboard    |
|  - Indexer            |
+-----------+-----------+
            |
            |
            v
+-----------------------+
|      Kali Linux       |
|                       |
|    Wazuh Agent        |
+-----------------------+
```

---

## Components

### Wazuh Server

Responsible for:

- Collecting endpoint logs
- Processing security events
- Generating alerts
- Mapping activity to MITRE ATT&CK

### Kali Linux Agent

Responsible for:

- Sending endpoint telemetry
- Monitoring authentication activity
- Monitoring process execution
- Monitoring file changes
- Reporting suspicious events

---

## Environment

| Component | Purpose |
|------------|----------|
| Wazuh Server | Security Monitoring |
| Kali Linux | Monitored Endpoint |
| VirtualBox | Virtualization Platform |

---

## Objectives

- Deploy and configure a Wazuh monitoring environment
- Connect a Linux endpoint to the Wazuh server
- Validate agent communication
- Prepare the environment for endpoint detection use cases

---

## Validation

The following validations were performed:

- Wazuh dashboard accessible
- Agent deployment completed
- Agent successfully connected
- Endpoint logs received by Wazuh
- MITRE ATT&CK dashboard operational

---
