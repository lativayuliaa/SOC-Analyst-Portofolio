# Case 01 - Nmap Detection

## Objective

Detect network reconnaissance activity performed from Kali Linux against a Windows 10 host.

## Attack Scenario

An attacker machine (Kali Linux) performs an Nmap scan against the victim system to identify exposed services.

## Attack Machine

192.168.56.102

## Victim Machine

192.168.56.103

## Command Used

sudo nmap -A 192.168.56.103

## Detection Method

Sysmon Event ID 3 (Network Connection)

## Investigation

Kibana Discover was used to analyze the generated logs.

## Findings

Source IP:

192.168.56.102

Destination IP:

192.168.56.103

Technique:

Network Service Discovery

## MITRE ATT&CK

T1046 - Network Service Discovery
