# MITRE ATT&CK Mapping

## Technique

T1543.003 - Create or Modify System Process: Windows Service

## Tactics

Persistence

Privilege Escalation

## Description

Adversaries may create or modify Windows services to maintain persistence or execute malicious payloads with elevated privileges.

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Event ID 7045 - A service was installed in the system

## Detection Method

Elastic Stack and Windows Event Logs

## ATT&CK Reference

https://attack.mitre.org/techniques/T1543/003/
