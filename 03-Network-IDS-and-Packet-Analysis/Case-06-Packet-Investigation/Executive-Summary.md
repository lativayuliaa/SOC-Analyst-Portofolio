# Executive Summary

## Incident Overview

A network forensic investigation was conducted using a packet capture associated with a SmartApeSG ClickFix campaign that delivered Remcos RAT.

The objective of the investigation was to identify the victim system, reconstruct the attack sequence, extract Indicators of Compromise (IOCs), and validate malicious infrastructure using external Threat Intelligence.

The investigation was performed entirely through network traffic analysis using Wireshark, supported by VirusTotal and WHOIS.

---

# Executive Findings

The investigation successfully reconstructed the complete attack sequence from the initial DNS request through encrypted HTTPS communication.

Multiple Indicators of Compromise (IOCs) were identified and validated.

The attacker relied on web-based delivery followed by encrypted TLS communication to conceal subsequent activity.

Although the malware payload itself could not be decrypted from the packet capture, network evidence strongly supports activity consistent with the SmartApeSG ClickFix campaign delivering Remcos RAT.

---

# Key Findings

## Victim

Internal Host

```
10.3.12.101
```

---

## Malicious Domains

```
forcebiturg.com
retrypoti.top
```

---

## External Infrastructure

```
159.65.191.64

24.199.121.166
```

---

## Initial Activity

The victim initiated HTTP requests to:

```
GET /boot

GET /proc
```

using:

```
curl/8.18.0
```

The web server immediately redirected the connection to HTTPS.

---

## Network Behavior

Observed attacker behavior included:

- DNS resolution
- HTTP communication
- HTTP redirection
- TLS handshake
- Encrypted TLS application data
- Large encrypted packet transfer

The communication pattern is consistent with malware delivery over encrypted channels.

---

# Threat Intelligence Assessment

External Threat Intelligence confirmed that:

- Both identified domains were classified as malicious by multiple security vendors.
- Both domains were registered immediately before the observed campaign.
- One domain was subsequently suspended by its registrar.

These findings significantly increased confidence in the investigation.

---

# Business Impact

If observed in a production environment, this activity could indicate:

- Initial malware execution
- Remote Access Trojan (RAT) deployment
- Potential command-and-control communication
- Unauthorized remote access
- Possible follow-on attacker activity

Immediate containment and endpoint investigation would be recommended.

---

# MITRE ATT&CK Summary

The observed activity maps primarily to:

| Tactic | Technique |
|---------|-----------|
| Resource Development | Acquire Infrastructure |
| Initial Access | Drive-by Compromise |
| Command and Control | Web Protocols |
| Command and Control | Encrypted Channel |

---

# Confidence Assessment

| Finding | Confidence |
|----------|------------|
| Victim Identification | High |
| Malicious Domains | High |
| DNS Findings | High |
| HTTP Analysis | High |
| TLS Analysis | High |
| Threat Intelligence Validation | High |
| Malware Family Attribution | Medium |

The malware payload itself remained encrypted; therefore, attribution relies on network evidence, IOC correlation, dataset context, and Threat Intelligence.

---

# Recommendations

Based on the investigation, the following actions are recommended:

- Block all identified malicious domains.
- Block associated external IP addresses.
- Hunt for additional hosts communicating with the same infrastructure.
- Search SIEM logs for the identified User-Agent and domains.
- Perform endpoint forensic analysis on affected systems.
- Monitor future DNS queries for the identified Indicators of Compromise.
- Update IDS/IPS detection rules using the extracted IOCs.

---

# Conclusion

This investigation demonstrates a complete network-based incident response workflow.

The attack chain was successfully reconstructed through packet analysis, infrastructure investigation, IOC extraction, and Threat Intelligence validation.

Although encrypted communication prevented direct payload inspection, the available evidence provides high confidence that the observed activity is consistent with a SmartApeSG ClickFix campaign associated with Remcos RAT.

The investigation highlights the importance of combining network forensics with Threat Intelligence to identify and understand modern malware campaigns.
