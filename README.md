# Network Traffic Analysis & Service Discovery

## Project Overview
This project demonstrates the capture and analysis of DNS traffic and service discovery using **Kali Linux**. The goal was to resolve the domain `jedha.co` and analyze its network footprint.

## 1. DNS Analysis Details
* **Target Domain:** `jedha.co`
* **Protocol:** DNS over UDP (Port 53)
* **Transaction ID:** `0x49f8` (Observed in Wireshark)
* **Resolution Result:** The domain resolved to IP address **198.202.211.1**.

### Security Findings
* **TTL Analysis:** A very low **TTL of 5 seconds** was detected, indicating high-availability load balancing or dynamic DNS.
* **Query Filtering:** Attempting an `ANY` query returned an `RFC8482` HINFO record, showing protection against DNS amplification attacks.
* **Mail Infrastructure:** MX records point to Google Workspace (`aspmx.l.google.com`).

## 2. Service Discovery (Nmap Scan)
I performed a port scan to identify active services on the target.

### Scan Results:
| Port | State | Service | Description |
|------|-------|---------|-------------|
| 80/tcp | open | http | Standard web traffic |
| 443/tcp | open | https | Secure web traffic (SSL/TLS) |
| 8080/tcp | open | http-proxy | Alternative web service or proxy |

## 3. Methodology (Tools Used)
* **OS:** Kali Linux (User: `pereyra`)
* **Network Analysis:** Wireshark
* **DNS Lookup:** `dig jedha.co`
* **Port Scanning:** `nmap -F jedha.co`

## Evidence
![Wireshark Capture](image_73a7fb.png)

## Conclusion
The target machine is a web server hosting services on both standard and alternative ports. The presence of port 8080 suggests an additional layer of service, likely for internal proxying or staging.
