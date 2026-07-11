# Lessons Learned

## Overview
This document summarizes the technical and operational lessons learned during the network forensic investigation of the SmartApeSG ClickFix campaign.

---

# Operational Takeaways

* **Lesson 1 — Never Trust a Single Indicator:** DNS queries or newly observed domains alone do not confirm a compromise. High confidence is achieved by correlating independent data points (DNS, HTTP, TLS, WHOIS, and Threat Intel).
* **Lesson 2 — Metadata Value over Encrypted Streams:** While HTTPS prevents direct payload parsing, encrypted sessions expose metadata like destination SNI domains, IPs, certificates, and traffic volumes.
* **Lesson 3 — Recently Registered Domains Require Attention:** Both malicious domains were registered on the same day as the campaign. Monitoring newly registered domains helps catch phishing and malware staging infrastructure early.
* **Lesson 4 — User-Agents Reveal Automation:** The identification of `curl/8.18.0` indicates programmatic command execution rather than human web browsing. Command-line tools driving outbound workstation web traffic warrant immediate inspection.
