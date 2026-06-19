# MITRE ATT&CK Mapping

## Technique

T1218 - System Binary Proxy Execution

## Tactic

Defense Evasion

## Description

Adversaries may abuse trusted Windows binaries to execute commands and evade security controls. LOLBins allow attackers to leverage legitimate tools already present on the operating system.

## Victim Host

Windows 10 (192.168.56.103)

## Observed Events

* Sysmon Event ID 1 - Process Creation

## Detection Method

Elastic Stack and Sysmon telemetry

## ATT&CK Reference

https://attack.mitre.org/techniques/T1218/
