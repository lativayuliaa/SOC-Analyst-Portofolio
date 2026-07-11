# Indicators of Compromise (IOC)

## Overview
This document summarizes all Indicators of Compromise (IOCs) identified during the network forensic investigation of the GuLoader and AgentTesla malware infection.

---

# IOC Directory Tables

## Email Indicators
| Indicator Value | Type | Description |
| :--- | :--- | :--- |
| **SHIPPING DOC \|\| INVOICE NO. USF/23-26/072 IGR23110** | Email Subject | Phishing theme lure header |
| **shipping@paramee.com** | Sender Address | Spoofed or compromised sender |
| **inv.5234353.rar** | File Name | Malicious delivery attachment |

## Domain Indicators
| Domain Name | Role | Reputation Status |
| :--- | :--- | :--- |
| **drive.google.com** | Payload Staging Infrastructure | Legitimate Abused Service |
| **drive.usercontent.google.com** | Component Component hosting | Legitimate Abused Service |
| **ip-api.com** | External IP Discovery Tool | Legitimate Abused Service |
| **ftp.corwineagles.com** | Attacker Exfiltration Gateway | Malicious / Compromised |
| **corwineagles.com** | Parent Infrastructure Domain | Malicious (18/91 Flags) |

## IP Address Indicators
| IP Address | Protocol / Role | Associated Destination |
| :--- | :--- | :--- |
| **162.241.123.75** | Port 21 / FTP Exfiltration Destination | ftp.corwineagles.com |
| **142.251.186.132** | Port 443 / HTTPS Component Download | Google Infrastructure |
| **142.250.115.138** | Port 443 / HTTPS Component Download | Google Infrastructure |
| **208.95.112.14** | Port 80 / HTTP Public IP Lookup | ip-api.com service |

## Recovered FTP Credentials
| Type | Extracted Plaintext Token | Recovery Context |
| :--- | :--- | :--- |
| **Username** | `edunis@corwineagles.com` | Recovered from FTP USER frame |
| **Password** | `cCycU=91vup7` | Recovered from FTP PASS frame |

## Compromised Victim Artifacts
| Host Attribute | Value | Source Evidence |
| :--- | :--- | :--- |
| **Victim System Hostname** | `DESKTOP-W7F98GR` | Embedded in exfiltrated file name |
| **Victim Local Username** | `tyler` | Embedded in exfiltrated file name |

## Exfiltrated Data Files
| Exfiltrated Filename | Payload Content Description |
| :--- | :--- |
| **PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html** | Harvested browser password store report |
| **Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt** | Stolen Thunderbird application contacts |

---

# Summary Metrics
* **Email Indicators:** 3
* **Domains:** 5
* **IP Addresses:** 4
* **FTP Credentials:** 2
* **Victim Artifacts:** 2
* **Exfiltrated Files:** 2

---

# Infrastructure Assessment
Threat intelligence lookups show that `corwineagles.com` is an established domain created on **2019-01-17** and registered via *PublicDomainRegistry*. While the hosting IP address itself was not flagged as natively malicious by all vendors, the domain name has multiple historical ties to phishing distribution and malware deployment. This indicates that the attacker chose to compromise and abuse an established legacy domain to evade reputation filters rather than registering a new domain.
