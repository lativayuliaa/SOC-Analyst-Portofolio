# Executive Summary

## 📌 Incident Overview

A network forensic investigation was conducted using a packet capture associated with a **SmartApeSG ClickFix** campaign delivering **Remcos RAT**. The objective of the investigation was to identify the victim system, reconstruct the attack sequence, extract Indicators of Compromise (IOCs), and validate the malicious infrastructure using external Threat Intelligence sources.

The investigation was performed entirely through **network traffic analysis** using **Wireshark**, with additional validation provided by **VirusTotal** and **WHOIS**.

![SmartApeSG ClickFix Activity for Remcos RAT Campaign Overview](assets/ss-01-smartapesg-clickfix-activity-for-remcos-rat.png)

---

## 🎯 Executive Findings

The investigation successfully reconstructed the complete attack sequence from the initial DNS request through encrypted HTTPS communication.

Multiple Indicators of Compromise (IOCs) were identified and validated. The attacker relied on web-based delivery followed by encrypted TLS communication to conceal subsequent activity.

Although the malware payload itself could not be decrypted from the packet capture, the collected network evidence strongly supports activity consistent with the **SmartApeSG ClickFix** campaign delivering **Remcos RAT**.

---

## 🔍 Key Findings

### Victim

**Internal Host**

```text
10.3.12.101
```

### Malicious Domains

```text
forcebiturg.com
retrypoti.top
```

### External Infrastructure

```text
159.65.191.64
24.199.121.166
```

### Initial Activity

The victim initiated HTTP requests using the following resources:

- `GET /boot`
- `GET /proc`

The requests were generated using the following User-Agent:

```text
curl/8.18.0
```

The web server immediately redirected the client to HTTPS.

---

### Network Behavior

The observed attack sequence included:

- DNS resolution
- HTTP communication
- HTTP redirection (301)
- TLS handshake
- Encrypted TLS application data
- Large encrypted packet transfer

---

### Threat Intelligence Assessment

External Threat Intelligence confirmed that:

- Both identified domains were classified as malicious by multiple security vendors.
- Both domains were registered shortly before the observed campaign.
- One of the domains was subsequently suspended by its registrar.

---

### Business Impact

If observed in a production environment, this activity could indicate:

- Initial malware execution
- Remote Access Trojan (RAT) deployment
- Command-and-Control (C2) communication
- Unauthorized remote access
- Additional post-compromise attacker activity

---

## 🗺️ MITRE ATT&CK Summary

| Tactic | Technique |
| :--- | :--- |
| Resource Development | Acquire Infrastructure |
| Initial Access | Drive-by Compromise |
| Command and Control | Application Layer Protocol: Web Protocols |
| Command and Control | Encrypted Communication Channel |

---

## 📊 Confidence Assessment

| Finding | Confidence |
| :--- | :---: |
| Victim Identification | 🟠 High |
| Malicious Domains | 🟠 High |
| DNS Findings | 🟠 High |
| HTTP Analysis | 🟠 High |
| TLS Analysis | 🟠 High |
| Threat Intelligence Validation | 🟠 High |
| Malware Family Attribution | 🟡 Medium |

---

## 🛡️ Recommendations

- Block all identified malicious domains and associated IP addresses.
- Hunt for additional hosts communicating with the same infrastructure.
- Search SIEM logs for the identified User-Agent and malicious domains.
- Perform endpoint forensic analysis on affected systems.
- Update IDS/IPS detection rules using the extracted Indicators of Compromise (IOCs).
