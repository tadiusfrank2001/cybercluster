# 🔐 pfSense Firewall Configuration

## Overview

`pfSense` is a powerful open-source firewall and router operating system built on FreeBSD. It provides essential security services such as:

- Stateful packet filtering
- Network Address Translation (NAT)
- VPN support
- Intrusion Detection/Prevention (with tools like Snort)
- Web-based management interface

In this cyber lab, pfSense acts as the **central gateway and firewall**, connecting isolated internal networks to the external internet while enforcing traffic segmentation, logging, and intrusion detection.

---

## 🖥️ VM Configuration

- **Hypervisor**: UTM (macOS)
- **ISO**: `pfSense-CE-X.Y.Z-RELEASE-amd64.iso`
- **Resources**:
  - 4 GB RAM
  - 8 GB virtual disk
- **Network Adapters** (3 total):
  - `em0`: **WAN** – NAT/Shared Adapter (DHCP)
  - `em1`: **LAN1** – Emulated VLAN Internal Network 1 (192.168.100.1/24)
  - `em2`: **LAN2** – Emulated VLAN Internal Network 2 (192.168.101.1/24)

---
## 🔧 Installation Steps

1. Booted from pfSense ISO installer.
2. Selected:
   - Partition: Entire disk (UFS)
   - Partition scheme: GPT
3. Completed installation and rebooted.
4. Removed ISO media to avoid reinstall loop.

---

## 🔌 Interface Assignment on Pfsense

1. Select the appropriate number on the Pfesense CLI for setting **Interface Assignments**

3. Set the following configs for each interface:
   
- **WAN** → `em0` (NAT to host for internet access)
- **LAN1** → `em1` (192.168.100.1/24)
- **LAN2** → `em2` (192.168.101.1/24)
- VLAN tagging: **Disabled**

---

## 🌐 IP Configuration

1. Select the appropriate number on the Pfesense CLI for setting **IP Configuration**

2. Set the following configs for each interface:

### LAN1 Interface (`em1`)
- **Static IP**: `192.168.100.1/24`
- **DHCP Range**: `192.168.100.10` – `192.168.100.100`

### LAN2 Interface (`em2`)
- **Static IP**: `192.168.101.1/24`
- **DHCP Range**: (Optional, TBD based on connected devices)

### WAN Interface (`em0`)
- **DHCP from Host Network**

---


