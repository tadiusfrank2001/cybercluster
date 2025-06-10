# 💀 Kali Linux (Attacker VM)

## 📄 Overview

Kali Linux is a Debian-based, open-source distribution built specifically for **penetration testing**, **digital forensics**, and **ethical hacking**. It includes powerful tools like:

- 🛠️ Metasploit Framework
- 🛰️ Nmap
- 🔍 Wireshark
- 🔓 Burp Suite
- and many more...

In this cyber lab, Kali Linux acts as the **attacker system**, used to simulate real-world offensive operations. It targets vulnerable machines like Metasploitable2 and interacts with security infrastructure (e.g., pfSense and Snort) to trigger and validate detection events. **Kali operates on an isolated subnet (192.168.101.0/24)**, segmented from the target machine (Metasploitable2), and routed through **pfSense**. This simulates a real-world internal attack where **lateral movement** must pass through security enforcement points.

---

## ⚙️ Virtual Machine Configuration

| Resource       | Value              |
|----------------|--------------------|
| RAM            | 4 GB               |
| CPU            | 2 cores            |
| Disk           | 40 GB              |
| Network Adapter| Emulated VLAN (LAN 2 via pfSense) |
| IP Address     | `192.168.101.20/24` (via DHCP)   |
| Gateway        | `192.168.101.1` (pfSense LAN2)   |

---

## 🖥️ VM Installation (UTM on macOS)

1. Download Kali ISO from [https://www.kali.org/get-kali/](https://www.kali.org/get-kali/)
2. Create a new VM in **UTM**:
   - OS Type: Debian/Linux
   - Memory: 4 GB
   - CPU: 2 Cores
   - Disk: 40 GB
   - Boot from ISO
3. Proceed with **Graphical Install**:
   - Hostname: `kali`
   - Full disk guided partitioning
   - Create root/admin user
4. Install GRUB bootloader
5. Eject ISO and reboot

---

## 🌐 Network Setup

| Setting         | Value                        |
|-----------------|------------------------------|
| Adapter Type    | Emulated VLAN                |
| Connected to    | pfSense LAN2 (192.168.101.0/24) |
| IP Address      | Assigned by pfSense via DHCP |

To verify network config:

```bash
ip a
```
the IP should be in the IP range set in pfsense so from **192.168.101.2 to 192.168.101.100**.

---

## 🪢 Confirm Network Connectivity

Confirm connectivity to the pfSense gateway:

```bash
ping 192.168.101.1
```
Confirm connectivity to Metasploitable2 (via routing):

```bash
ping 192.168.100.99
```
---

## 🛠️ Post-Install Checklist

 1. Perform system updates:

```bash
sudo apt update && sudo apt upgrade -y
```
2. Install any additional tools (optional):

```bash
sudo apt install net-tools nmap wireshark burpsuite -y
```

