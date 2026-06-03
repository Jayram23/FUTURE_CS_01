# ZAP Session Notes — OWASP Juice Shop Passive Audit

## Session Info
- Tool: OWASP ZAP 2.17.0
- Proxy: localhost:8080
- Mode: Standard (Manual Explore)
- Target: https://demo.owasp-juice.shop/
- Date: 2026-06-03

## Steps Followed

1. Launched ZAP → New Session
2. Set Firefox proxy to localhost:8080
3. Imported ZAP root CA certificate into Firefox
4. Used Manual Explore → entered target URL → launched Firefox
5. Browsed homepage, product listing, cookie banner
6. Let ZAP passive scanner run automatically in background
7. Checked Alerts tab after 10 minutes of browsing

## Alerts Detected by ZAP (raw count: 13)

| Alert | Count |
|---|---|
| Content Security Policy (CSP) Header Not Set | 1 |
| Mauvaise configuration inter-domaines (Cross-Domain) | 1 |
| Missing Anti-Clickjacking Header | 2 |
| Referer Exposes Session ID | 1 |
| Session ID in URL Rewrite | 5 |
| Private IP Disclosure | 1 |
| Strict-Transport-Security Header Not Set | 1 |
| Timestamp Disclosure - Unix | 1 |
| X-Content-Type-Options Header Missing | 4 |
| Information Disclosure - Browser localStorage | 1 |
| Information Disclosure - Browser sessionStorage | 1 |

## HTTP Headers Observed (key absences)

- ❌ Content-Security-Policy → NOT PRESENT
- ❌ Strict-Transport-Security → NOT PRESENT  
- ❌ X-Frame-Options → NOT PRESENT
- ❌ X-Content-Type-Options → NOT PRESENT
- ❌ Referrer-Policy → NOT PRESENT
- ✅ Content-Type → Present
- ✅ Connection → Present

## Notes

- ZAP HUD was disabled during the session (clean passive mode)
- socket.io endpoints returned 503/504 errors — backend partially unavailable
- JS bundles visible: main.js, polyfills.js (large, minified Angular app)
- Cookie banner references "fruit cookies" — marketing, not security-relevant
- localStorage observed to contain app state including auth-related keys
