# 💀 Kali Linux (Attacker VM)

## 📄 Overview

Kali Linux is a Debian-based, open-source distribution built specifically for **penetration testing**, **digital forensics**, and **ethical hacking**. It includes powerful tools like:

- 🛠️ Metasploit Framework
- 🛰️ Nmap
- 🔍 Wireshark
- 🔓 Burp Suite
- and many more...

In this cyber lab, Kali Linux acts as the **attacker system**, used to simulate real-world offensive operations. It targets vulnerable machines like Metasploitable2 and interacts with security infrastructure (e.g., pfSense and Snort) to trigger and validate detection events.

---

## ⚙️ Virtual Machine Configuration

| Setting        | Value                    |
|----------------|--------------------------|
| **RAM**        | 4 GB                     |
| **CPU**        | 2 cores                  |
| **Disk**       | 40 GB                    |
| **Network**    | Emulated VLAN (Internal) |

> 🧠 Kali resides on its own subnet managed by pfsense which can route traffic between Kali and the metaploitable VM.

---

