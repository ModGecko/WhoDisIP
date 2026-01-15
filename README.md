# WhoDisIP | ModGecko Intelligence

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![Version](https://img.shields.io/badge/Version-1.0.0-green)
![License](https://img.shields.io/badge/License-GPLv3-blue)

> [!TIP]
> ### 🛠️ Need Support or Installation Help?
> We provide **free** official support and professional services for this tool.
>
> * **❓ General Support:** View our available support channels at [modgecko.com/support](https://modgecko.com/support).
> * **🐛 Bug Reports:** Found a glitch? Please open a public [Issue on GitHub](https://github.com/ModGecko/whodisip/issues).
> * **🔐 Security Issues:** Do **NOT** report security flaws on GitHub. Please submit a private ticket via our [Support Center](https://modgecko.com/support).

**Maintained by the [ModGecko Team](https://modgecko.com)**

---

## Overview

**WhoDisIP** is a lightweight, browser-based OSINT (Open Source Intelligence) tool designed for rapid infrastructure mapping. It allows developers and sysadmins to quickly resolve domains, identify hosting providers, and retrieve geolocation data without needing backend infrastructure.

It supports:
- **Dual-Stack Resolution:** Automatically detects and resolves IPv4 and IPv6.
- **Infrastructure Mapping:** Identifies ISP, Hosting Provider, and Organization.
- **Registrar Data:** Fetches Domain Registrar info via RDAP.
- **DNS Recon:** Retrieves active Nameservers.
- **Geolocation:** Provides City, Country, and Timezone data.

---

## Stable Release

✅ **v1.0.0 Stable** - This tool is production-ready.
While fully stable, please report any edge-case bugs via the **GitHub Issues** page so they can be addressed in future updates.

---

## Requirements

- **Modern Web Browser** (Chrome, Firefox, Edge, Safari) with ES6+ support.
- **Internet Connection** (Required for API lookups).
- *Optional:* A static web server (Apache, Nginx, or GitHub Pages) for hosting.

---

## Installation

WhoDisIP is designed as a **Single File Application**. It requires no PHP, Node.js, or database backend.

1. Clone or download this repository.
2. Upload the `index.html` file to your web server (or open it locally in your browser).
3. The tool works immediately—no configuration required.

---

## Usage

1. Enter a **Target** into the input field.
   - Accepts **IPv4** (e.g., `8.8.8.8`)
   - Accepts **IPv6** (e.g., `2001:4860:4860::8888`)
   - Accepts **Domains** (e.g., `modgecko.com`)
2. Click **Analyze**.
3. The card will expand to show:
   - Resolved IP Address
   - Nameservers (if Domain)
   - Hosting Provider / ISP
   - Domain Registrar
   - Physical Location & Timezone

---

## ⚠️ Architecture & Limits (Important)

WhoDisIP operates entirely **Client-Side**, meaning all API requests are made directly from the **User's Browser**, not your web server.

### 🚀 Zero-Risk Scaling
Because the tool relies on the visitor's browser to fetch data, **your server's IP address is never used** for API lookups.
- **No Server Bans:** You can host this tool for thousands of concurrent users without fear of your server getting blacklisted by API providers.
- **Distributed Rate Limits:** API usage limits apply to the **User's IP**. If one user spams the tool and gets rate-limited, it **does not affect** other users or your server.

### 🛑 Specific API Limits (Per User)
The tool queries public endpoints which enforce the following limits **per visitor**:
- **Geolocation (ipwho.is):** ~45 requests per minute.
- **Registrar Data (rdap.org):** ~10 requests per 10 seconds.
- **DNS Resolution (dns.google):** ~1,500 requests per second.

*If a user exceeds these limits, they will receive an HTTP 429 error until their cooldown period expires.*

### 🔒 Privacy & CORS
- **Browser Privacy Extensions:** Aggressive privacy tools (e.g., uBlock Origin, Privacy Badger) may block the cross-origin (CORS) requests needed to fetch data.
- **Registrar Privacy (GDPR):** Some domain registries redact ownership data in their RDAP responses. In these cases, the tool will display "Restricted/Manual".

---

## APIs & Data Sources

To maintain a serverless architecture, WhoDisIP queries the following public endpoints directly from the client's browser:

- **Google DNS** (DoH) - For A/AAAA/NS record resolution.
- **RDAP.org** - For Registrar identification.
- **IPWho.is** - For Geolocation and ISP data.

---

## Changelog

**v1.0.0**
- Initial stable release.
- Added support for IPv4 and IPv6 inputs.
- Integrated Dark/Light mode toggle with persistence.
- Added responsive mobile layout.
- Implemented error handling for failed DNS resolutions.

---

## License

This project is licensed under the **[GPLv3 License](LICENSE)**.  
You may use, modify, and redistribute the module **as long as credit is preserved** and derivatives remain open source.

---

## Credits

- **[ModGecko](https://modgecko.com)** – Project Maintainer
- **[@Pyryxe (Hadrian)](https://github.com/Pyryxe)** – Lead Developer