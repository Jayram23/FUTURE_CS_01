# 🔐 Vulnerability Assessment Report — OWASP Juice Shop

> **Passive Web Application Security Audit**  
> Target: [https://demo.owasp-juice.shop/](https://demo.owasp-juice.shop/)  
> Date: June 3, 2026  
> Type: Passive scan only — no exploitation performed

---

## 📋 Project Overview

This repository contains the deliverables of a passive security assessment performed on the OWASP Juice Shop demo application. The goal was to identify common web vulnerabilities using only passive observation techniques — no active attacks, no data extraction, no exploitation.

This project was conducted as part of a cybersecurity training curriculum, applying real-world methodology to a safe, intentionally vulnerable target.

---

## 🛠️ Tools Used

| Tool | Version | Purpose |
|---|---|---|
| OWASP ZAP | 2.17.0 | Intercepting proxy — passive scan |
| Firefox | 140 | Browser for manual exploration |
| Firefox DevTools | Built-in | HTTP header inspection |
| Firefox Profiler | Built-in | Client-side JS / network analysis |
| Kali Linux | Rolling | Testing environment (VMware) |

---

## 📁 Repository Structure

```
juice-shop-audit/
│
├── README.md                        ← This file
│
├── report/
│   └── Vulnerability_Assessment_Report_JuiceShop_2026.docx
│
├── evidence/
│   ├── 01_zap_welcome_session.png           ← ZAP 2.17.0 initial setup
│   ├── 02_zap_manual_explore_target.png     ← ZAP proxying Juice Shop
│   ├── 03_juiceshop_homepage.png            ← Target application (Kali/Firefox)
│   ├── 04_zap_alerts_panel.png             ← 13 alerts from passive scan
│   └── 05_firefox_profiler_js.png          ← JS execution analysis
│
└── tools/
    └── zap_session_notes.md                ← Methodology notes
```

---

## 🔍 Findings Summary

| ID | Vulnerability | Risk |
|---|---|---|
| F-01 | Missing Content Security Policy (CSP) Header | 🟡 MEDIUM |
| F-02 | Missing HTTP Strict Transport Security (HSTS) | 🟡 MEDIUM |
| F-03 | Missing Anti-Clickjacking Header | 🟡 MEDIUM |
| F-04 | Session ID Exposed in URL | 🔴 HIGH |
| F-05 | Referer Header Leaks Session ID | 🟡 MEDIUM |
| F-06 | Timestamp Disclosure (Unix) | 🟢 LOW |
| F-07 | X-Content-Type-Options Header Missing | 🟢 LOW |
| F-08 | Private IP Address Disclosure | 🟢 LOW |
| F-09 | Sensitive Data in Browser Storage | 🟡 MEDIUM |
| F-10 | Cross-Domain Misconfiguration (CORS) | 🟡 MEDIUM |

**Total: 1 High · 6 Medium · 3 Low**

---

## ⚙️ Methodology

All testing was **passive only**:

1. OWASP ZAP configured as proxy on `localhost:8080`
2. Firefox routed through ZAP, HUD disabled
3. Manual browsing of the Juice Shop application
4. ZAP passive scanner automatically flagged anomalies in HTTP traffic
5. HTTP headers manually verified in Firefox DevTools
6. Client-side behaviour observed with Firefox Performance Profiler

No forms were submitted with attack payloads. No authentication was attempted. No data was read, modified, or exfiltrated.

---

## 📄 Report

The full professional report is available in `/report/`. It includes:

- Executive Summary (business language)
- Scope and methodology description
- 10 detailed finding cards with business impact and remediation steps
- Risk classification summary table
- Conclusion and prioritised recommendations

---

## ⚠️ Disclaimer

This assessment was performed exclusively on a publicly available, intentionally vulnerable demo application operated by the OWASP Foundation for educational purposes. No real systems, real users, or real data were involved. This project is intended solely for educational and portfolio demonstration purposes.

---

## 👤 Author

**Cybersecurity Student —  Cybersecurity Track**  
Tools: Kali Linux · OWASP ZAP · Firefox · VMware Workstation
