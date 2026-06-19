# MITRE ATT&CK Mapping

## Technique

T1059.001 - PowerShell

## Tactics

Execution

Defense Evasion

## Description

Adversaries commonly use Base64-encoded PowerShell commands to conceal malicious actions and bypass simple detection mechanisms.

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Sysmon Event ID 1 - Process Creation

## Detection Method

Elastic Stack and Sysmon telemetry

## ATT&CK Reference

https://attack.mitre.org/techniques/T1059/001/
