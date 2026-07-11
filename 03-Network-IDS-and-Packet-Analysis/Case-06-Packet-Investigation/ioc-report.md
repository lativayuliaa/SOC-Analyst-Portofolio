# Indicators of Compromise (IOC) Report

## Overview
This report documents all Indicators of Compromise (IOCs) identified during the investigation of the SmartApeSG ClickFix campaign associated with Remcos RAT.

---

# IOC Summary

| IOC | Type | Source | Confidence | Description |
| :--- | :--- | :--- | :--- | :--- |
| **10.3.12.101** | Victim IP | Endpoint Statistics | High | Internal host identified as the victim system |
| **159.65.191.64** | External IP | DNS Response | High | IP address hosting forcebiturg.com |
| **24.199.121.166** | External IP | DNS Response | Medium | IP address associated with retrypoti.top |
| **forcebiturg.com** | Domain | DNS + HTTP | High | Initial malicious domain contacted by the victim |
| **retrypoti.top** | Domain | TLS Cert + DNS | High | Secondary malicious infrastructure |
| **GET /boot** | URI | HTTP Request | High | Initial HTTP request issued by the victim |
| **GET /proc** | URI | HTTP Request | High | Secondary HTTP request observed before TLS redirect |
| **curl/8.18.0** | User-Agent | HTTP Header | Medium | Indicates automated scripting activity |
| **HTTP 301** | HTTP Response | HTTP Response | High | Redirect from HTTP to HTTPS |
| **TLS App Data** | TLS Protocol | TLS Stream | High | Encrypted payload delivery channel |

---

# Infrastructure Details

## forcebiturg.com
* **Type:** Domain
* **Role:** Initial Web Infrastructure Staging
* **Resolved IP:** 159.65.191.64
* **Registration Date:** 2026-03-12
* **Evidence Sources:** DNS Query/Response, HTTP Host Header, VirusTotal, WHOIS

## retrypoti.top
* **Type:** Domain
* **Role:** Secondary Encryption Infrastructure
* **Resolved IP:** 24.199.121.166
* **Registration Date:** 2026-03-12
* **Evidence Sources:** TLS Certificate SNI, DNS Response, VirusTotal, WHOIS
