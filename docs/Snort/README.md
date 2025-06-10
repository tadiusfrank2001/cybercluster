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

### 3. Update Snort Rules

1. Navigate to the **Updates** tab.
2. Click **Update Rules**
3. Wait for the ruleset to download and install.

---
### 4. Add Snort to LAN Interfaces

You’ll configure Snort on **both LAN1 and LAN2** to capture traffic from **Metasploitable2** and **Kali Linux**.

#### LAN1 (192.168.100.0/24)

1. Go to: `Services → Snort → Interfaces`
2. Click `+ Add`
3. Select interface (e.g., `em1`)
4. Enable the following:
   - `✔️ Enable Snort on this interface`
   - `✔️ Block Offenders` *(optional IDS/IPS mode, for the this set up we will disable this it will block our attacker scans lol)*
5. Choose desired rule categories:
   - `attack-responses`, `policy`, `scan`, etc.
6. Click **Save**

#### LAN2 (192.168.101.0/24)

Repeat the steps above but select the **second LAN interface** (e.g., `em2`) for Kali Linux.

---

### 5. Start Snort

1. Return to the **Interfaces** tab
2. Click the **Start (▶)** button next to each interface (LAN1 and LAN2)
3. ✅ Confirm Snort shows as **Running** on both

---

### 6. View Alerts

1. Navigate to: `Services → Snort → Alerts`
2. Observe logs as attacks are launched from Kali toward Metasploitable2
3. Example alerts may include:
   - Port scanning (Nmap)
   - Shellcode execution
   - Exploit attempts

---

