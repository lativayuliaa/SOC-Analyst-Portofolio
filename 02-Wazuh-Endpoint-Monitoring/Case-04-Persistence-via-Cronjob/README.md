# Persistence via Cronjob

## Overview

This case demonstrates how Wazuh can detect persistence-related activity on a Linux endpoint through cron job modifications.

Cron jobs are commonly abused by attackers to maintain persistence by automatically executing commands or scripts at scheduled intervals.

---

## Scenario

A new cron job was created on the monitored Kali Linux endpoint.

The objective was to verify that Wazuh detected changes related to cron configuration and generated corresponding alerts.

---

## Attack Simulation

The following cron job was added:

```text
*/5 * * * * echo "Persistence Test" >> /tmp/persistence.log
```

The cron configuration was modified using:

```bash
crontab -e
```

---

## Detection Method

Wazuh monitored file system changes and persistence-related configuration files through File Integrity Monitoring (FIM) and Whodata.

Relevant monitored locations include:

* User crontabs
* System cron configuration files
* Scheduled task files

---

## Findings

Wazuh successfully detected changes associated with cron configuration modifications.

Observed information:

* User account
* File path
* Timestamp
* Modification activity
* Persistence-related configuration changes

---

## Security Impact

Unauthorized cron jobs may indicate:

* Persistence mechanisms
* Malware execution
* Backdoor installation
* Scheduled malicious tasks

---

## Outcome

The objective was successfully completed.

Wazuh generated alerts related to cron configuration changes and provided visibility into persistence-related activity.

---
