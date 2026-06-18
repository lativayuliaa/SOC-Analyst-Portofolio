# MITRE ATT&CK Mapping

## Technique

T1046 - Network Service Discovery

## Tactic

Discovery

## Description

The attacker used Nmap to enumerate services exposed by the target host. Network service discovery is commonly used during the reconnaissance phase to identify open ports and running services.

## Attack Source

Kali Linux (192.168.56.102)

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Sysmon Event ID 3 - Network Connection

## Detection Method

Elastic Stack and Sysmon telemetry

## ATT&CK Reference

https://attack.mitre.org/techniques/T1046/
