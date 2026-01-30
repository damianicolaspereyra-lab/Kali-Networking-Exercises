# Network Traffic Analysis: DNS Resolution

## Project Overview
This project demonstrates the capture and analysis of DNS traffic using **Kali Linux**, the **`dig`** utility, and **Wireshark**. The goal was to resolve the domain `jedha.co` and analyze the underlying network protocols and security measures.

## Technical Details
* **Target Domain:** `jedha.co`
* **Protocol:** DNS over UDP (Port 53)
* **Transaction ID:** `0x49f8` (Observed in Wireshark)
* **Resolution Result:** The domain resolved to IP address **198.202.211.1**.

## Security Findings
* **TTL Analysis:** A very low **TTL of 5 seconds** was detected, indicating high-availability load balancing or dynamic DNS.
* **Query Filtering:** Attempting an `ANY` query returned an `RFC8482` HINFO record, showing protection against DNS amplification attacks.
* **Mail Infrastructure:** MX records point to Google Workspace (`aspmx.l.google.com`).

## Tools Used
* Kali Linux (User: pereyra)
* Wireshark (Network Protocol Analyzer)
* Dig (DNS Lookup Utility)
