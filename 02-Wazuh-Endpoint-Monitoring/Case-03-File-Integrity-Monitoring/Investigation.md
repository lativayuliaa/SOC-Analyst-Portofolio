# Investigation Report

## Alert Summary

Wazuh generated File Integrity Monitoring alerts indicating file creation, modification, and deletion activity on the monitored Linux endpoint.

---

## Investigation Steps

### Step 1 - Review Alert

The generated alerts indicated changes to monitored files within the configured directory.

---

### Step 2 - Identify Affected File

The affected file path was reviewed.

Information collected:

* File name
* File path
* Timestamp
* User account

---

### Step 3 - Analyze Activity

The sequence of activity observed was:

1. File created
2. File modified
3. File deleted

This activity was successfully recorded by Wazuh.

---

### Step 4 - Determine Impact

Although performed in a controlled lab environment, similar activity may indicate:

* Malware execution
* Data manipulation
* Evidence destruction
* Unauthorized user activity

---

## Classification

Suspicious

---

## MITRE ATT&CK

* T1565.001 - Stored Data Manipulation
* T1070.004 - File Deletion

---

## Conclusion

Wazuh successfully detected and recorded file system changes using File Integrity Monitoring with Whodata enabled.

The generated alerts provide valuable visibility into file activity and can help security analysts identify unauthorized modifications and potential attacker behavior.
