# 🎯 Metasploitable2 (Target VM)

## Overview

`Metasploitable2` is a purposefully vulnerable Linux-based virtual machine developed by Rapid7. It’s widely used as a sandbox for:

- Practicing offensive security techniques
- Testing IDS/IPS detection capabilities
- Simulating real-world exploitation scenarios

In this cyber lab, Metasploitable2 acts as the **victim machine** on an isolated internal network, allowing structured attacks from Kali Linux and monitoring via Snort on pfSense.

---

## 💾 Installation & Configuration

### 1. 🔽 Download VM Image

- Source: [Metasploitable2 – SourceForge](https://sourceforge.net/projects/metasploitable/)
- File Format: `.vmdk`
- Convert for UTM compatibility by using this command in your host CLI:
  ```bash
  qemu-img convert -f vmdk -O qcow2 input.vmdk output.qcow2
  ```
## 2. 🖥️ Create Virtual Machine (UTM)

| Setting   | Value                      |
|-----------|----------------------------|
| Name      | Metasploitable-2           |
| OS Type   | Linux (Ubuntu 8.04)        |
| RAM       | 512 MB                     |
| CPU       | 1 core                     |
| Disk      | Attach converted `.qcow2`  |

---

## 3. 🌐 Network Configuration

Make sure the metaploitable VM has a network adapter set to Emulated VLAN!

- **Network Adapter**: `Internal Network`
- **Connected to the same virtual LAN as**:
  - Kali Linux (Attacker)
  - pfSense (Firewall)
- In UTM: Choose **Emulated VLAN**

This ensures all traffic routes through pfSense.

---

## 🔐 Login & Access

1. Insert username and password
- **Username**: `msfadmin`  
- **Password**: `msfadmin`


2. After logging in, check the IP address:

```bash
ifconfig
```

📝 Expected IP: 192.168.100.x (assigned via pfSense DHCP)

3. Confirm connectivity to the pfSense gateway:

```bash 
ping 192.168.100.1
```

✅ A successful ping means Metasploitable2 is live and reachable in the lab network.
