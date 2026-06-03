🔐 Web Application Vulnerability Assessment — OWASP Juice Shop

Author: Marina | Master 1 Cybersecurity — IPNET University (2025–2026)
Target: https://demo.owasp-juice.shop/
Tools: OWASP ZAP 2.17.0 (Passive Scan) | Firefox DevTools
Type: Passive Security Assessment — No exploitation performed
Date: June 2026

📁 Repository Structure
juice-shop-audit/
│
├── README.md
│
├── report/
│   └── Vulnerability_Assessment_Report.docx
│
└── evidence/
    ├── 01_ZAP_Welcome_Screen.png
    ├── 02_ZAP_Manual_Explore_Setup.png
    ├── 03_Juice_Shop_Homepage.png
    ├── 04_ZAP_Alerts_Panel.png
    └── 05_Firefox_DevTools_Headers.png
    
🎯 Objectives

This project documents a passive-only web application security assessment performed on the OWASP Juice Shop demo application.

The main objectives were:

Identify missing or misconfigured HTTP security headers
Detect information disclosure issues
Review client-side security weaknesses
Assess baseline security posture of the application

No exploitation or active attack techniques were performed.

🔍 Methodology

The assessment was conducted using a strictly passive approach:

Manual navigation of the application
OWASP ZAP Passive Scan (no active scanning enabled)
HTTP response analysis via Firefox Developer Tools
Review of browser storage and client-side behaviour

👉 No authentication bypass, fuzzing, brute force, or attack simulation was performed.

🔍 Key Findings Summary
#	Vulnerability	Risk Level
1	Missing Content Security Policy (CSP) Header	🟠 Medium
2	Missing Clickjacking Protection (X-Frame-Options / frame-ancestors)	🟠 Medium
3	Missing Strict-Transport-Security (HSTS) Header	🟠 Medium
4	Missing X-Content-Type-Options Header	🟡 Low
5	Potential Sensitive Data Exposure via Client-Side Storage	🔴 High
6	Insecure Session Handling Observed in Application Behaviour	🔴 High
7	Internal Information Disclosure via HTTP Responses	🟡 Low
8	Metadata / Timestamp Exposure in Client Responses	🟡 Low
9	Browser Storage Information Exposure (Local / Session Storage)	🟡 Low

📊 Summary
Total ZAP alerts: 13
Consolidated findings: 9 categorized security issues
🛠️ Tools Used
Tool	Version	Purpose
OWASP ZAP	2.17.0	Passive vulnerability detection
Firefox DevTools	Latest	HTTP header & storage inspection
Kali Linux	Latest	Testing environment
⚠️ Scope & Limitations
Target application: OWASP Juice Shop demo instance
Testing limited to publicly accessible features
Passive analysis only (no active scanning or exploitation)
Results reflect observed security posture only
📊 Business Impact

The findings indicate common security misconfigurations typically found in early-stage or intentionally vulnerable web applications.

While no critical server-side vulnerabilities were confirmed, the following risks are relevant from a business perspective:

Increased exposure to client-side attacks (e.g., XSS)
Lack of browser-level security protections
Potential information leakage useful for attackers during reconnaissance
Weak baseline security hardening practices

📬 Key Recommendations

To improve security posture, the following controls should be implemented:

Enforce a strict Content Security Policy (CSP)
Enable HSTS (HTTP Strict Transport Security)
Add X-Frame-Options / frame-ancestors to prevent clickjacking
Configure X-Content-Type-Options: nosniff
Secure session handling (HttpOnly, Secure, SameSite cookies)
Minimize information disclosure in HTTP responses

🧾 Conclusion

This passive security assessment highlights several common web application security misconfigurations affecting browser-level protection mechanisms.

Although no critical vulnerabilities were identified, implementing baseline security headers and strengthening client-side security controls would significantly improve the application's resilience against common web attacks.

📌 Notes
This project is intended for educational and portfolio purposes
The target application is intentionally vulnerable and publicly provided for security training
No unauthorized systems were tested
