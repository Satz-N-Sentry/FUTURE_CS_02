# FUTURE_CS_02 — Phishing Email Detection & Awareness Report
## SAIZERO — Ground Zero Defence
### *Every shadow has a hunter* 🐺

---

## Overview

This repository contains a professional phishing email detection and awareness
analysis conducted as part of the Future Interns Cybersecurity Internship 2026.

Three real-world phishing email samples were collected from public honeypot
repositories and analysed using multiple industry-standard tools to identify
attack patterns, social engineering techniques, and malicious infrastructure
used by threat actors.

---

## Target Organisation

This analysis was conducted using a simulated client profile
(Pinnacle Capital Group LLC) for training purposes as part of
the Future Interns Cybersecurity Internship 2026. The phishing
email samples analysed are real samples collected from public
honeypot repositories.

| Field | Details |
|-------|---------|
| Client | Pinnacle Capital Group LLC *(Simulated)* |
| Industry | Financial Services & Investment |
| Location | New York, NY, USA |
| Contact | Michael D. Carter — CISO |
| Assessment Date | March 2026 |
| Classification | Educational — Training Exercise |

---

## Samples Analysed

### sample-1000.eml — Brazilian Tax Refund Scam

| Field | Details |
|-------|---------|
| Subject | Liberacao de IRPF - 6NwlyfzWcsNerv0 |
| Sender | prestonconstance587@gmail.com |
| Date | 26 July 2023 17:59:01 UTC |
| Language | Portuguese (Brazilian) |
| Attack Type | Social Engineering — Malware Delivery via Attachment |
| OWASP | SE-01 |
| Technique | Legitimate Service Abuse — Free Gmail Account |
| SPF / DKIM / DMARC | PASS / PASS / PASS (p=none — not enforced) |
| Blacklist | Hop 3 flagged by Microsoft EOP |
| Classification | CONFIRMED PHISHING |

**Key Indicators:**
- Free Gmail used — tax authority never sends from Gmail
- Campaign tracking code in subject: 6NwlyfzWcsNerv0
- Fake protocol number: 4793122145117905827
- Malicious attachment present
- Delivered in 6 seconds — automated bulk campaign

---

### sample-1002.eml — Microsoft Account Impersonation

| Field | Details |
|-------|---------|
| Subject | Microsoft account unusual signin activity |
| Sender | no-reply@access-accsecurity.com |
| Sending Domain | thcultarfdes.co.uk |
| Sending IP | 89.144.44.2 (Warsaw, Poland) |
| Date | 26 July 2023 21:13:36 UTC |
| Attack Type | Brand Impersonation — Credential Harvesting + Victim Tracking |
| OWASP | A07:2021 — Identification and Authentication Failures |
| Technique | Domain Spoofing + Hidden Tracking Pixel |
| SPF / DKIM / DMARC | NONE / NONE / PERMERROR |
| Blacklist | Hop 4 flagged |
| Classification | CONFIRMED PHISHING |

**Key Indicators:**
- All SPF/DKIM/DMARC checks FAILED
- All links route to attacker Gmail — not Microsoft
- Tracking pixel thebandalisty.com — 6/98 VirusTotal detections
- 731 URLScan records — confirmed large-scale mass campaign
- Sending IP from Warsaw Poland — Microsoft is US-based
- From domain access-accsecurity.com never registered

---

### sample-1003.eml — XRP Ripple Crypto Scam

| Field | Details |
|-------|---------|
| Subject | More benefits from Ripple with the Allocation Program |
| Sender | coindesk@mg.areafellowship.com |
| Sending Domain | mg.areafellowship.com (compromised church subdomain) |
| Sending IP | 198.61.254.55 (Mailgun Technologies — Chicago) |
| Phishing Domain | mail123-ripple.net (Russian hosted) |
| Date | 27 July 2023 15:06:03 UTC |
| Attack Type | Financial Fraud — Cryptocurrency Investment Scam |
| OWASP | A05:2021 — Security Misconfiguration |
| Technique | Legitimate Service Abuse — Mailgun + Fake Landing Page |
| SPF / DKIM / DMARC | PASS / PASS / bestguesspass |
| Blacklist | Hop 5 flagged |
| Classification | CONFIRMED PHISHING |

**Key Indicators:**
- Mailgun abused via compromised church subdomain
- SCL:9 maximum spam score — still delivered
- Origin server completely hidden (Hop 0 = unknown)
- All links go to Russian-hosted fake Ripple website
- Victim email hex-encoded in URL — individual tracking
- NICENIC Chinese throwaway registrar
- Real court ruling used as social engineering bait
- Blockchain transactions irreversible — no recovery

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Thunderbird | Open .eml files — view email body and extract raw headers |
| MXToolbox | Header analysis — SPF, DKIM, DMARC, blacklist detection |
| Google Admin Toolbox | Hop timeline — email routing path and delay analysis |
| VirusTotal | URL and domain multi-vendor malicious detection |
| URLScan.io | Safe URL inspection and page screenshot without clicking |
| AbuseIPDB | Sending IP address abuse history and confidence score |
| WHOIS | Domain registration date, registrar, and ownership check |
| Git | Version control — track and push evidence to repository |
| GitHub | Public repository hosting for submission deliverables |

---

## Analysis Methodology

1. **Email Inspection** — Open .eml in Thunderbird, read body, identify social engineering
2. **Header Extraction** — View raw source (Ctrl+U), copy full headers
3. **Authentication Analysis** — Paste into MXToolbox and Google Admin Toolbox
4. **IP Investigation** — Check sending IP via AbuseIPDB
5. **Domain Investigation** — Check sender domain via WHOIS
6. **URL Analysis** — Inspect links via URLScan.io and VirusTotal
7. **Indicator Documentation** — Record all phishing red flags per sample
8. **Risk Classification** — Classify as Safe / Suspicious / Phishing

---

## Risk Classification Summary

| Sample | Attack Type | OWASP | Risk | Verdict |
|--------|-------------|-------|------|---------|
| sample-1000 | Social Engineering — Malware Delivery | SE-01 | HIGH | PHISHING |
| sample-1002 | Brand Impersonation — Credential Harvesting | A07:2021 | CRITICAL | PHISHING |
| sample-1003 | Financial Fraud — Crypto Investment Scam | A05:2021 | CRITICAL | PHISHING |

---

## Repository Structure
```
FUTURE_CS_02/
├── evidence/
│   ├── sample_1000_analysis.txt
│   ├── sample_1002_analysis.txt
│   └── sample_1003_analysis.txt
├── screenshots/
│   ├── sample_1000_thunder.png
│   ├── sample_1000_mxtool.png
│   ├── sample_1000_googletool.png
│   ├── sample_1002_thunderbird.png
│   ├── sample_1002_mxtool.png
│   ├── sample_1002_googltool.png
│   ├── sample_1002_Abuseip.png
│   ├── sample_1002_virustotal.png
│   ├── sample_1002_urlscan.png
│   ├── sample_1002_whois.png
│   ├── sample_1003_googletool.png
│   ├── sample_1003_abuseip.png
│   ├── sample_1003_virustotal.png
│   ├── sample_1003_whois.png
│   └── sample_1003_yrlscan.png
├── samples/
│   ├── sample-1000.eml
│   ├── sample-1002.eml
│   └── sample-1003.eml
├── reports/
│   └── SAIZERO_Phishing_Final.pdf
└── README.md
```

---

## Assessor

**Satheesh Nithiananthan** (CyberLycan)
SAIZERO — Ground Zero Defence
Future Interns Cybersecurity Internship 2026

*Every shadow has a hunter* 🐺
