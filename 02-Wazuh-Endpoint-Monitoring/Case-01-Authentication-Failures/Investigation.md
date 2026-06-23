# Investigation Report

## Alert Summary

Wazuh generated alerts indicating failed authentication attempts on the monitored Linux endpoint.

---

## Investigation Steps

### Step 1 - Review Alert

The alert indicated authentication failures recorded by the Linux authentication subsystem.

---

### Step 2 - Identify Target Account

The affected account was identified from the authentication logs.

Information reviewed:

- Username
- Hostname
- Timestamp

---

### Step 3 - Analyze Event Frequency

Multiple failed authentication attempts were observed within a short period.

This behavior may indicate:

- User error
- Password guessing
- Brute force activity

---

### Step 4 - Determine Impact

No successful authentication was observed during the test.

The activity was classified as suspicious but did not result in unauthorized access.

---

## Classification

Suspicious

---

## MITRE ATT&CK

- T1110 - Brute Force

---

## Conclusion

Authentication failure events were successfully detected by Wazuh.

The alerts demonstrate Wazuh's capability to monitor credential-related attacks and provide visibility into suspicious login activity on Linux endpoints.
