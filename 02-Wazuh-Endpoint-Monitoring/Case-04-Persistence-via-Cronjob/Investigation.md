# Investigation Report

## Alert Summary

Wazuh generated alerts indicating modifications to cron-related configuration files on the monitored Linux endpoint.

---

## Investigation Steps

### Step 1 - Review Alert

The alert indicated that a monitored cron configuration file had been modified.

---

### Step 2 - Identify User Activity

The responsible user account was identified through Whodata information and file monitoring events.

Information reviewed:

* Username
* Timestamp
* Modified file path

---

### Step 3 - Analyze Configuration Changes

The modified cron entry was reviewed to determine its purpose and potential security impact.

Observed entry:

```text
*/5 * * * * echo "Persistence Test" >> /tmp/persistence.log
```

---

### Step 4 - Determine Impact

The cron job establishes an automated scheduled task that executes repeatedly.

In a real-world environment, similar activity could indicate:

* Persistence mechanisms
* Malware scheduling
* Unauthorized administrative actions

---

## Classification

Suspicious

---

## MITRE ATT&CK

* T1053.003 - Cron

---

## Conclusion

Wazuh successfully detected persistence-related activity through monitoring of cron configuration changes.

The generated alerts provide visibility into scheduled task creation and can help analysts identify unauthorized persistence mechanisms on Linux endpoints.
