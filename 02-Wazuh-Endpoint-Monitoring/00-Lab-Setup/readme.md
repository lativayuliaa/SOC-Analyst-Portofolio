# Wazuh Lab Setup

## 📌 Overview

This lab demonstrates the deployment of a single-node **Wazuh SIEM/XDR** environment for endpoint monitoring and security event analysis.

The environment consists of a Wazuh server and a monitored Kali Linux endpoint. After deployment, the lab verifies agent communication, telemetry ingestion, and dashboard visibility, providing a foundation for endpoint detection, threat hunting, and MITRE ATT&CK mapping.

---

## 🏗️ Lab Architecture

```text
+---------------------------------------+
|             Wazuh Server              |
|                                       |
|  - Wazuh Manager (Core Engine)        |
|  - Wazuh Dashboard (Visualization)    |
|  - Wazuh Indexer (Search & Storage)   |
+-------------------+-------------------+
                    |
                    | Telemetry
                    v
+---------------------------------------+
|            Kali Linux Host            |
|                                       |
|  - Wazuh Agent                        |
+---------------------------------------+
```

---

## ⚙️ Core Components

### 🖥️ Wazuh Server

The Wazuh server acts as the central monitoring platform and is responsible for:

- Collecting endpoint telemetry from connected agents
- Processing security events using Wazuh detection rules
- Generating security alerts
- Storing indexed event data
- Visualizing events through the Wazuh Dashboard
- Mapping alerts to the MITRE ATT&CK framework

### 🐧 Kali Linux Endpoint

The Kali Linux machine is configured as a monitored endpoint running the Wazuh Agent.

The agent collects telemetry including:

- Authentication events
- Process execution
- File Integrity Monitoring (FIM)
- System logs
- Security-related events

---

## 💻 Lab Environment

| Component | Role |
| :--- | :--- |
| **Wazuh Server** | Centralized SIEM/XDR Platform |
| **Kali Linux** | Monitored Endpoint |
| **Wazuh Agent** | Endpoint Telemetry Collection |
| **VirtualBox** | Virtualization Platform |

---

## 🎯 Lab Objectives

- Deploy a single-node Wazuh server
- Install and register a Wazuh Agent on Kali Linux
- Establish secure communication between the agent and the server
- Verify endpoint telemetry ingestion
- Prepare the environment for security monitoring and detection engineering

---

## ✅ Deployment Validation

The deployment was verified using the following validation steps.

### 1. Wazuh Dashboard Access

The Wazuh web dashboard is accessible, and all core services are operating normally.

### 2. Agent Installation

The Wazuh Agent was successfully installed and registered on the Kali Linux endpoint.

### 3. Agent Communication

The agent status is **Active**, confirming successful communication with the Wazuh Manager.

### 4. Telemetry Ingestion

Security events generated on the endpoint are successfully collected, indexed, and displayed in the Wazuh Dashboard.

---

## 🚀 Next Steps

After completing the deployment, the environment is ready for endpoint monitoring and security use cases, including:

- File Integrity Monitoring (FIM)
- Process Monitoring
- Authentication Monitoring
- Log Analysis
- Threat Detection
- MITRE ATT&CK Mapping
