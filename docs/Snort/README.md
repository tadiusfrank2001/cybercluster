# 🛡️ Snort Intrusion Detection System

## 📖 Overview

**Snort** is an open-source Intrusion Detection and Prevention System (IDS/IPS) developed by Cisco. It performs **real-time traffic analysis** and **deep packet inspection** to detect a variety of attacks, including port scans, malware, and exploit attempts.

In this lab, Snort is installed on the **pfSense firewall**, acting as the monitoring and alerting layer between internal lab networks:

- `LAN1 (192.168.100.0/24)` – Metasploitable2 (Target VM)
- `LAN2 (192.168.101.0/24)` – Kali Linux (Attacker VM)

Snort monitors and optionally blocks suspicious activity between attacker and target systems, simulating a realistic network defense posture.

---

## 🛠️ Setup Instructions

### 1. Install Snort via pfSense Package Manager

1. Open a browser in Kali Linux and access pfSense at:  
   `https://192.168.100.1`
2. Navigate to:  
   `System → Package Manager → Available Packages`
3. Search for **Snort**, click **Install**, and confirm.

---

### 2️⃣ Configure Global Settings

1. Go to:  
   `Services → Snort → Global Settings`
2. Select a rule provider:
   - ✅ **Emerging Threats Open** *(recommended for labs bc it's open source and does not require registration)*
   - (Optional) Add your **Oinkcode** if using Snort VRT
3. Enable:
   - `✔️ Update Rules Automatically`
4. Click **Save**

---

