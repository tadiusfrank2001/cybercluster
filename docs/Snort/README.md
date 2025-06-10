# 🛡️ Snort Intrusion Detection System

## 📖 Overview

**Snort** is an open-source Intrusion Detection and Prevention System (IDS/IPS) developed by Cisco. It performs **real-time traffic analysis** and **deep packet inspection** to detect a variety of attacks, including port scans, malware, and exploit attempts.

In this lab, Snort is installed on the **pfSense firewall**, acting as the monitoring and alerting layer between internal lab networks:

- `LAN1 (192.168.100.0/24)` – Metasploitable2 (Target VM)
- `LAN2 (192.168.101.0/24)` – Kali Linux (Attacker VM)

Snort monitors and optionally blocks suspicious activity between attacker and target systems, simulating a realistic network defense posture.

---

