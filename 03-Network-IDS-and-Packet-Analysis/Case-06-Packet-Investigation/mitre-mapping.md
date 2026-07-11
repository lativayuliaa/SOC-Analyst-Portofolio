# MITRE ATT&CK Mapping

## Overview
This document maps the observed attacker behavior to the MITRE ATT&CK Enterprise Framework based on the network evidence recovered during packet analysis.

---

## 🎯 Tactical Alignment Matrix

| Tactic | Technique | ID | Evidence Profile Match | Confidence |
| :--- | :--- | :--- | :--- | :--- |
| **Resource Development** | Acquire Infrastructure: Domains | T1583.001 | Provisioning of `forcebiturg.com` and `retrypoti.top` on campaign launch day. | 🟠 High |
| **Resource Development** | Acquire Infrastructure: Server | T1583.005 | Deployment of cloud-hosted public IP systems (`159.65.191.64`). | 🟡 Medium |
| **Initial Access** | Drive-by Compromise | T1189 | Victim host directed to access malicious web staging endpoints. | 🟠 High |
| **Command and Control** | Application Layer Protocol | T1071 | Execution of HTTP request structures and HTTPS data channels. | 🟠 High |
| **Command and Control** | Encrypted Channel | T1573 | Use of high-volume TLS application streams to obscure binary payload transmission. | 🟠 High |

---

## 🧩 Technical Execution Mapping

### T1189 — Drive-by Compromise
The victim endpoint initiated unencrypted HTTP queries (`GET /boot` and `GET /proc`) to an external web node. The target server responded with an automated HTTP `301 Moved Permanently` code, forcing the browser or script to upgrade the connection to an encrypted channel. This transition pattern is typical of web-based drive-by compromise vectors used to deliver second-stage malware payloads.

### T1573 — Encrypted Channel
Following the protocol upgrade, the connection migrated to a high-volume TLS session. The transfer of large data blocks, characterized by dense `PSH, ACK` flag arrays, was used to obfuscate the binary payload transmission. This approach prevents signature-matching perimeter controls from inspecting the traffic content without active decryption capabilities.
