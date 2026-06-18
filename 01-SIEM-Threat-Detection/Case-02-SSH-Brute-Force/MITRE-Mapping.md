# MITRE ATT&CK Mapping

## Technique

T1110 - Brute Force

## Tactic

Credential Access

## Description

The attacker attempted multiple SSH logins against the target host using different passwords. After several failed authentication attempts, valid credentials were discovered, resulting in a successful login.

## Attack Source

Kali Linux (192.168.56.102)

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Event ID 4625 – Failed Logon
* Event ID 4624 – Successful Logon

## Detection Method

Elastic Stack and Windows Security Event Logs

## ATT&CK Reference

https://attack.mitre.org/techniques/T1110/
