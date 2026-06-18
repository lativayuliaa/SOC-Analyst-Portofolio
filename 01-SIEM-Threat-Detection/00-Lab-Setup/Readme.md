# Lab Setup

## Objective

Build a SOC home lab to collect and analyze security events using Elastic Stack.

## Environment

| Machine | Purpose | IP Address |
|-----------|---------|------------|
| Host Laptop | Elasticsearch + Kibana | 192.168.56.1 |
| Windows 10 VM | Victim + Sysmon + Winlogbeat | 192.168.56.103 |
| Kali Linux VM | Attacker | 192.168.56.102 |

## Components

- Elasticsearch 8.11
- Kibana 8.11
- Sysmon
- Winlogbeat
- OpenSSH Server
- Kali Linux
