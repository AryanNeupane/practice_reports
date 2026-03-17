# 🛡️ Cybersecurity Reconnaissance Report  
## Target: graceintlgroup.com  

---

## 📌 1. Basic Information

- **Domain:** graceintlgroup.com  
- **IP Address:** 46.202.186.47  
- **Hosting Provider:** Hostinger  
- **Server Location:** Indonesia (ID)  
- **Web Server:** LiteSpeed  

---

## 🌐 2. Technology Stack

### CMS & Platform
- WordPress 6.8.5  

### Plugins & Tools
- Slider Revolution 6.6.4  
- Site Kit 1.150.0  

### Analytics & Tracking
- Google Analytics  
- Facebook Pixel  
- Google Tag Manager  

### Frontend Technologies
- Svelte  
- GSAP  

### JavaScript Libraries
- jQuery 3.7.1  
- jQuery UI 1.13.3  
- jQuery Migrate 3.4.1  
- DataTables 2.2.2  
- Moment.js 2.29.4  
- Hammer.js 2.0.6  
- Isotope  
- Masonry  
- LazySizes  
- core-js 3.35.0  
- Spin.js  
- lit-html 3.2.1  
- lit-element 4.1.1  

### Graphics & Visualization
- particles.js  
- Chart.js  

### Fonts & APIs
- Google Font API  
- Font Awesome  

### Security
- reCAPTCHA  

### Other Features
- RSS  
- Open Graph  
- HTTP/3  

### Backend Technologies
- PHP 8.2.30  
- MySQL / MariaDB 11.8.3  

### Maps Integration
- Leaflet 1.3.1  
- Google Maps  

### Hosting & Performance
- Hosting: Hostinger  
- Lazy Loading: LazySizes  

---

## 🔍 3. Network Scan (Nmap Results)

### Open Ports

| Port | Service | Version |
|------|--------|--------|
| 21   | FTP    | ProFTPD / KnFTPD |
| 80   | HTTP   | LiteSpeed |
| 443  | HTTPS  | LiteSpeed |
| 3306 | MySQL  | MariaDB 11.8.3 |
| 65002 | SSH   | OpenSSH 8.7 |

---

### Key Observations

- HTTP/HTTPS returns **403 Forbidden**
- FTP service is exposed
- MySQL service publicly accessible
- SSH running on **non-standard port (65002)**

---

## 🧭 4. Subdomain Enumeration

### Total Found: 55 Subdomains

#### Important Subdomains
- www.graceintlgroup.com  
- portal.graceintlgroup.com  
- study.graceintlgroup.com  
- seminar.graceintlgroup.com  
- fair.graceintlgroup.com  
- australia.graceintlgroup.com  
- india.graceintlgroup.com  
- kenya.graceintlgroup.com  
- worldcup.graceintlgroup.com  

#### Sensitive/Interesting Subdomains
- cpanel.graceintlgroup.com  
- webmail.graceintlgroup.com  
- mail.graceintlgroup.com  
- webdisk.graceintlgroup.com  

---

## 📂 5. Directory Enumeration (Dirsearch)

### Findings

- `/.git` directory exists but **access is forbidden (403)**  
- `/.git/config`, `/.git/HEAD` also restricted  
- `/.git.json` returned **503 Service Unavailable**  
- Encoded path:
  - `/%2e%2e;/test` → redirects to `/test/`  

---

## 🧠 6. OS Detection

- Likely OS: Linux  
- Kernel range: 4.x – 5.x  
- No exact match (scan conditions not ideal)

---

## 🌍 7. WHOIS Summary

- **IP Range:** 46.202.184.0/22  
- **Organization:** Private Customer  
- **ASN:** AS47583  
- **Abuse Contact:** report@abuseradar.com  

---

## ⚠️ 8. Potential Security Observations

### Medium Risk
- FTP service exposed (Port 21)  
- MySQL publicly accessible (Port 3306)  
- SSH on non-standard port (65002)  

### Low Risk / Informational
- `.git` directory detected but protected  
- Multiple subdomains increase attack surface  
- Use of third-party plugins (WordPress ecosystem risk)

---

## 📊 9. Summary

The target is a **WordPress-based web application** hosted on **Hostinger**, using a **LiteSpeed server**.  

Key highlights:
- Multiple exposed services (FTP, MySQL, SSH)  
- Large number of subdomains  
- Modern frontend stack with many JS libraries  
- Protected but detectable `.git` repository  

---
