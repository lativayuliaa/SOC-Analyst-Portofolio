# MITRE ATT&CK Mapping

## Technique

T1059.001 - PowerShell

## Tactic

Execution

## Description

PowerShell was used to execute commands on the target system. PowerShell is commonly abused by adversaries for command execution, payload delivery, and post-exploitation activities.

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Sysmon Event ID 1 - Process Creation

## Detection Method

Elastic Stack and Sysmon telemetry

## ATT&CK Reference

https://attack.mitre.org/techniques/T1059/001/
