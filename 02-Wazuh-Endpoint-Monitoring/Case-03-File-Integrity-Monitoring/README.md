# File Integrity Monitoring (Whodata)

## Overview

This case demonstrates how Wazuh monitors file system activity using File Integrity Monitoring (FIM) with Whodata enabled.

Whodata provides visibility into file operations by identifying who modified a file, what action was performed, and when the change occurred.

---

## Scenario

A test file was created, modified, and deleted on the monitored Kali Linux endpoint.

The objective was to verify that Wazuh successfully detected file system changes and generated corresponding alerts.

---

## Attack Simulation

The following actions were performed:

```bash
mkdir ~/wazuh-test

touch payroll.xlsx

echo "confidential data" >> payroll.xlsx

rm payroll.xlsx
```

---

## Detection Method

Wazuh File Integrity Monitoring (FIM) was configured with Whodata enabled.

The agent monitored file activity and generated alerts when:

* A file was created
* A file was modified
* A file was deleted

---

## Findings

Wazuh successfully detected file operations performed on the monitored endpoint.

Observed information:

* File path
* User account
* Timestamp
* Action performed
* File status changes

---

## Security Impact

Unexpected file modifications may indicate:

* Malware activity
* Data tampering
* Insider threats
* Unauthorized access
* Evidence removal

---

## Outcome

The objective was successfully completed.

Wazuh generated alerts for file creation, modification, and deletion events and provided visibility into file system activity.

---
