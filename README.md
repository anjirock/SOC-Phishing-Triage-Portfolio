
# SOC Phishing Triage Portfolio

## Overview

This project simulates a SOC (Security Operations Centre)       
Analyst's end-to-end workflow for triaging user-reported
phishing threats. Three real-world phishing samples were
sourced from URLhaus (abuse.ch) and PhishTank (Cisco Talos
Intelligence), then investigated using industry-standard
OSINT and threat intelligence tools.

All samples were handled safely. Malicious URLs were
submitted as text only to reputation analysis platforms.
No malicious sites were visited directly at any point.

## Tools Used

| Tool | Purpose |
|------|---------|
| URLhaus (abuse.ch) | Malicious URL threat intelligence database |
| PhishTank (Cisco Talos) | Community phishing URL reporting platform |
| VirusTotal | Multi-vendor URL, domain, and file reputation |
| Google Admin Toolbox | Email header and authentication analysis |
| RDAP / WHOIS | Domain registration forensics |
| AbuseIPDB | IP address reputation and abuse history |
| URLScan.io | Safe visual page rendering and verdict |



## Investigation Workflow

Each sample was put through the same repeatable triage
process used in real SOC environments:
Source identification → URLhaus / PhishTank

URL reputation check → VirusTotal (multi-vendor)

Domain forensics → RDAP / WHOIS / DNS analysis

SSL analysis → Certificate timeline review

Header analysis → SPF / DKIM / DMARC checks

Triage decision → True Positive / False Positive

Incident report → Executive + Technical writeup

IOC extraction → Documented for SIEM/blocklists





## Reports

| ID | Phishing Type | VT Score | Verdict |
|----|--------------|----------|---------|
| [IR-2026-001](IR-2026-001_Credential_Harvesting_RBC) | Banking Credential Harvesting — RBC Royal Bank | 23/92 | True Positive |
| [IR-2026-002](IR-2026-002_Malicious_Attachment_ConnectWise) | Malicious File Download / BEC — ConnectWise RAT | 13/92 | True Positive |
| [IR-2026-003](IR-2026-003_Brand_Impersonation_Amazon) | Brand Impersonation — Amazon Prime | 0/92* | True Positive |

> **IR-2026-003 Note:** The 0/92 VirusTotal result was not
> a false negative — it was caused by active scanner evasion
> (HTTP 403 cloaking) and a sub-16-hour domain age placing
> it inside the detection gap window. Forensic analysis of
> RDAP registration data, DNS TTL configuration, SSL
> certificate timeline, Cloudflare proxy usage, and DGA
> naming patterns confirmed True Positive classification.
> This case demonstrates the critical importance of
> contextual analyst judgement when automated tools are
> defeated by evasion techniques.



## Sample Comparison

| | IR-2026-001 | IR-2026-002 | IR-2026-003 |
|--|-------------|-------------|-------------|
| **Brand targeted** | RBC Royal Bank | Microsoft Teams | Amazon Prime |
| **VT detections** | 23/92 | 13/92 | 0/92 |
| **Domain type** | Purpose-built fake | Compromised legit site | DGA-generated |
| **Infrastructure** | Direct hosting | Hacked WordPress | Cloudflare-proxied |
| **Evasion used** | None | Legitimate domain reputation | HTTP 403 + proxy |
| **Detection method** | Automated vendor flags | Automated vendor flags | Forensic/contextual |
| **Verdict** | True Positive | True Positive | True Positive |



## Key Skills Demonstrated

- Threat intelligence sourcing (URLhaus, PhishTank)
- Multi-vendor URL reputation analysis (VirusTotal)
- Email header forensics (SPF / DKIM / DMARC)
- DNS record and WHOIS / RDAP investigation
- SSL certificate timeline forensic analysis
- Domain Generation Algorithm (DGA) identification
- Cloudflare reverse proxy evasion recognition
- Compromised legitimate website vs purpose-built
  malicious domain distinction
- IOC extraction and structured documentation
- True Positive classification under tool evasion
- Professional incident report writing
- Containment and remediation planning



## Repository Structure

SOC-Phishing-Triage-Portfolio/
├── README.md
├── reports/
│   ├── IR-2026-001_Credential_Harvesting_RBC.pdf
│   ├── IR-2026-002_Malicious_Attachment_ConnectWise.pdf
│   └── IR-2026-003_Brand_Impersonation_Amazon.pdf
├── screenshots/
│   ├── VT_IR001_RBC_23-92_detection.png
│   ├── VT_IR002_ConnectWise_13-92_detection.png
│   ├── VT_IR003_Amazon_domain_RDAP.png
│   └── URLhaus_samples_overview.png
└── iocs/
    └── IOC_master_list.csv



## Disclaimer

All samples were obtained from public threat intelligence
platforms (URLhaus and PhishTank) for educational and
portfolio demonstration purposes only. No malicious
infrastructure was interacted with directly. All IOCs
are documented solely for defensive and awareness purposes.
This project was completed in a safe, controlled manner
consistent with responsible security research practices.


## Author

**[ANJILAIAH DYAVARI]**
Aspiring SOC Analyst | Newcastle upon Tyne, England, UK
[https://www.linkedin.com/in/anjilaiah-dyavari-96622118b/]
[https://github.com/anjirock]
