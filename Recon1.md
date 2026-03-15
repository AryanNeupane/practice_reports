
# Reconnaissance Report — hamropatro.com

## Target Information

| Field | Value |
|------|------|
| Domain | hamropatro.com |
| Website | https://www.hamropatro.com |
| Recon Date | 2026-03-15 |
| Recon Type | Passive + Basic Active Recon |
| Research Purpose | Cybersecurity Learning |

---

# 1. Objective

The objective of this reconnaissance exercise is to collect publicly available
information about the target domain **hamropatro.com** using multiple
reconnaissance tools.

This information helps identify:

- Domain registration details
- DNS infrastructure
- Web technologies
- Subdomains
- Hidden directories

Reconnaissance is the **first phase of penetration testing** and helps
security researchers understand the attack surface of a system.

---

# 2. Tools Used

| Tool | Purpose |
|-----|------|
| whois | Domain registration information |
| whatweb | Website technology fingerprinting |
| nslookup | DNS enumeration |
| dirsearch | Directory brute-force |
| sublist3r | Subdomain discovery |
| amass | Advanced OSINT subdomain enumeration |

---

# 3. WHOIS Analysis

## Command

```bash
whois hamropatro.com
````

## Key Findings

| Field         | Information              |
| ------------- | ------------------------ |
| Domain Name   | hamropatro.com           |
| Registrar     | GoDaddy                  |
| Creation Date | 2010-10-21               |
| Expiry Date   | 2026-10-21               |
| Domain Status | clientTransferProhibited |
| DNSSEC        | Not enabled              |

## Registrant Information

| Field   | Value                                                     |
| ------- | --------------------------------------------------------- |
| Name    | Shankar Uprety                                            |
| City    | Boston                                                    |
| State   | Massachusetts                                             |
| Country | United States                                             |
| Email   | [shankaruprety@gmail.com](mailto:shankaruprety@gmail.com) |
| Phone   | +1-617-329-1230                                           |

## Name Servers

```
NEWT.NS.CLOUDFLARE.COM
TANI.NS.CLOUDFLARE.COM
```

### Observations

* The domain has existed since **2010**.
* Domain registration is managed by **GoDaddy**.
* DNS is handled by **Cloudflare**, providing CDN and security services.

---

# 4. Web Technology Detection

## Command

```bash
whatweb hamropatro.com
```

## Results

| Technology         | Details             |
| ------------------ | ------------------- |
| Web Server         | Cloudflare          |
| Backend            | PHP 8.0.30          |
| JavaScript Library | jQuery              |
| Analytics          | Google Tag Manager  |
| Framework          | Open Graph Protocol |
| Cookies            | PHPSESSID, __cflb   |

## HTTP Redirect Behavior

```
http://hamropatro.com
   → redirect
https://hamropatro.com
   → redirect
https://www.hamropatro.com
```

## Security Headers Observed

| Header                      | Status  |
| --------------------------- | ------- |
| X-XSS-Protection            | Enabled |
| Access-Control-Allow-Origin | Present |
| Cloudflare Headers          | Present |

### Observations

* The website uses **Cloudflare CDN**.
* Backend appears to run **PHP version 8.0.30**.
* Session management uses **PHP session cookies**.

---

# 5. DNS Enumeration

## Command

```bash
nslookup hamropatro.com
```

## IPv4 Addresses

```
104.26.5.51
104.26.4.51
172.67.70.183
```

## IPv6 Addresses

```
2606:4700:20::681a:533
2606:4700:20::681a:433
2606:4700:20::ac43:46b7
```

### Observations

* Multiple IP addresses indicate **Cloudflare load balancing**.
* The origin server IP is hidden behind Cloudflare's proxy network.

---

# 6. Directory Enumeration

## Command

```bash
dirsearch -u hamropatro.com
```

## Scan Configuration

| Setting       | Value                    |
| ------------- | ------------------------ |
| Wordlist Size | 11,460                   |
| Threads       | 25                       |
| Extensions    | php, aspx, jsp, html, js |
| HTTP Method   | GET                      |

## Discovered Paths

```
/axis2-web/HappyAxis.jsp
/axis/happyaxis.jsp
/axis2/axis2-web/HappyAxis.jsp
/Citrix/AccessPlatform/auth/clientscripts/cookies.js
/engine/classes/swfupload/swfupload.swf
/engine/classes/swfupload/swfupload_f9.swf
/extjs/resources/charts.swf
/html/js/misc/swfupload/swfupload.swf
```

### Observations

* Several endpoints returned **HTTP 301 redirects**.
* Some paths reference **legacy upload libraries or frameworks**.
* No sensitive directories were exposed during this scan.

---

# 7. Subdomain Enumeration (Sublist3r)

## Command

```bash
sublist3r -d hamropatro.com
```

## Discovered Subdomains

```
www.hamropatro.com
app.hamropatro.com
english.hamropatro.com
health.hamropatro.com
l.hamropatro.com
recharge.hamropatro.com
remit.hamropatro.com
```

### Observations

* Multiple services are deployed across different subdomains.
* These may represent **separate applications or APIs**.

---

# 8. Subdomain Enumeration (Amass)

## Command

```bash
amass enum -d hamropatro.com
```

Amass performs advanced passive reconnaissance using sources such as:

* Certificate transparency logs
* Passive DNS databases
* Search engines
* Threat intelligence feeds

The scan successfully confirmed previously discovered subdomains.

---

# 9. Potential Attack Surface (Educational Analysis)

Possible areas for further testing include:

| Area             | Possible Testing            |
| ---------------- | --------------------------- |
| Web Application  | XSS, SQL Injection          |
| Session Cookies  | Session Hijacking           |
| Subdomains       | Misconfiguration            |
| Upload Libraries | File Upload Vulnerabilities |
| Backend Services | PHP-related vulnerabilities |



---

# 10. Key Learning Points

* Learned how **WHOIS reveals domain ownership information**.
* Identified **web technologies using WhatWeb**.
* Performed **DNS enumeration using nslookup**.
* Conducted **directory brute-force scanning**.
* Discovered **multiple subdomains using Sublist3r and Amass**.
* Observed how **Cloudflare hides origin server infrastructure**.

---

# 11. Conclusion

The reconnaissance process identified that **hamropatro.com** operates
using a Cloudflare-protected infrastructure with a **PHP-based backend**.

The domain has been active since **2010** and provides multiple services
through several subdomains. Cloudflare's proxy network obscures the origin
server IP, increasing protection against direct attacks.

Directory enumeration did not reveal sensitive directories in this scan,
but the presence of multiple subdomains indicates a broader attack surface
that could be assessed in further testing phases.

---

