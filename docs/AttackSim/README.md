# 🏹 Attack Simulation

This section outlines a complete offensive workflow executed from the Kali Linux attacker VM targeting the Metasploitable2 vulnerable host. The attack follows the Cyber Kill Chain model and demonstrates how reconnaissance, exploitation, and post-exploitation phases unfold in a controlled lab environment.


---

## 🔍 Reconnaissance (OSINT)

- **Netdiscover**: Identified live hosts within the 192.168.101.0/24 and 192.168.100.0/24 ranges.
```bash
netdiscover -r 192.168.100.0/24
```
Explanation:

   -r: Specifies the subnet range to scan.
  
- **Nmap (-sS, -A)**: Performed stealth SYN scans and full version detection to identify open ports and services on Metasploitable2.
```bash
nmap -sS -A 192.168.100.2
```
Explanation:

   -sS: Performs a TCP SYN scan (stealth scan).
   -A: Enables OS detection, version detection, script scanning, and traceroute.

- **WhatWeb**: Detected web technologies running on Metasploitable’s HTTP service (e.g., Apache, PHP).
- **Nikto**: Scanned for known web vulnerabilities, including directory traversal, outdated components, and insecure HTTP headers.
- **Burp Suite (Passive/Active Scan)**: Intercepted and analyzed HTTP traffic for potential injection points and misconfigurations.

--- 


