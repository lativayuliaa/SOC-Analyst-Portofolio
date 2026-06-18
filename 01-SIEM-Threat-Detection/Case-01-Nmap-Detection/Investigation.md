# Investigation Report

## Summary

Network reconnaissance activity was detected against the Windows 10 host. The activity originated from the Kali Linux machine and was observed through Sysmon network connection events.

## Timeline

1. The attacker initiated an Nmap scan.
2. Sysmon generated Event ID 3.
3. Winlogbeat forwarded the events to Elasticsearch.
4. Kibana was used to investigate the network activity.

## Source IP

192.168.56.102

## Destination IP

192.168.56.103

## Hostname

WINDOWS10

## Evidence

* Sysmon Event ID 3

## Findings

The observed activity is consistent with reconnaissance behavior used to identify open ports and services on the target system.

## MITRE ATT&CK

T1046 - Network Service Discovery

## Severity

Low

## Recommendations

* Monitor unusual network connections.
* Detect repeated port scanning activity.
* Generate alerts for reconnaissance patterns.
* Restrict unnecessary services exposed on endpoints.
