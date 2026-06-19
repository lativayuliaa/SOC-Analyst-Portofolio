# Investigation Report

## Summary

A new local account was created on the Windows 10 host. User account creation events are important because attackers frequently create additional accounts to maintain persistence and ensure continued access to compromised systems.

## Timeline

1. A command was executed to create a new local user.
2. Windows generated Event ID 4720.
3. Winlogbeat forwarded the event to Elasticsearch.
4. Kibana was used to investigate the event details.

## Hostname

WINDOWS10

## Creator Account

vboxuser

## New User

backupadmin

## Evidence

### Event ID 4720

User Account Created

## Findings

The observed activity is consistent with account creation behavior. In enterprise environments, unexpected account creation should be investigated because it may indicate persistence or privilege escalation attempts.

## MITRE ATT&CK

T1136.001 - Create Account: Local Account

## Severity

Medium

## Recommendations

* Monitor account creation events.
* Review newly created accounts regularly.
* Alert on unauthorized user creation activity.
* Implement least privilege principles.
* Restrict administrative access to trusted users only.
