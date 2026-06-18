# Investigation Report

## Summary

Multiple failed SSH authentication attempts were detected against the Windows 10 host. The activity originated from the Kali Linux machine and eventually resulted in a successful authentication.

## Timeline

1. The attacker initiated multiple SSH login attempts.
2. Several failed authentications generated Event ID 4625.
3. A valid credential was eventually used.
4. Event ID 4624 recorded a successful login.

## Source IP

192.168.56.102

## Destination IP

192.168.56.103

## Target User

vboxuser

## Hostname

WINDOWS10

## Evidence

### Failed Authentication

* Event ID 4625

### Successful Authentication

* Event ID 4624

## Findings

The attack pattern is consistent with a brute-force attempt targeting SSH credentials.

## MITRE ATT&CK

T1110 - Brute Force

## Severity

Medium

## Recommendation

* Enforce strong passwords.
* Implement account lockout policies.
* Monitor repeated failed authentication attempts.
* Generate alerts for excessive Event ID 4625 occurrences.
