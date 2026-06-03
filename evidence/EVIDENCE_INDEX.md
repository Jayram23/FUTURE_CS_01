# Evidence Index — OWASP Juice Shop Passive Audit

All screenshots were captured on 2026-06-03 during the live passive scan session.

| File | Description | Section in Report |
|---|---|---|
| `01_zap_welcome_session.png` | OWASP ZAP 2.17.0 — initial welcome screen, new session loaded, proxy on localhost:8080 | Section 3 — Methodology |
| `02_zap_manual_explore_target.png` | ZAP Manual Explore panel with target URL set to https://demo.owasp-juice.shop/ — HTTP history showing live traffic, 2 Medium alerts already flagged | Section 3 — Methodology |
| `03_juiceshop_homepage.png` | OWASP Juice Shop homepage loaded in Firefox on Kali Linux — product listing visible, cookie consent banner present | Cover Page / Section 2 |
| `04_zap_alerts_panel.png` | ZAP Alerts tab — full list of 13 alerts including Missing Anti-Clickjacking Header (detail view), CSP Not Set, HSTS Not Set, Session ID in URL (x5), Private IP Disclosure, localStorage/sessionStorage disclosure | Section 4 — Findings |
| `05_firefox_profiler_js.png` | Firefox Performance Profiler — call tree view showing JavaScript execution on demo.owasp-juice.shop: main.js and polyfills.js bundles, doClose function detail, 86% JS / 14% DOM breakdown | Section 3 — Methodology |

## Screenshot Naming Convention

```
[ID]_[tool]_[description].png
```

## Environment

- OS: Kali Linux (VMware Workstation on Windows host)
- Browser: Firefox 140
- Resolution: 1920×1080 / 1920×835 (various)
- ZAP Version: 2.17.0
