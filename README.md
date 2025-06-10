# 🧠 CyberCluster: A Virtualized Cybersecurity Lab for Real-World Attack & Defense Scenarios

**CyberCluster** is a self-contained, fully virtual cybersecurity lab designed to emulate enterprise-grade attack and defense scenarios using open-source tools and virtualization. Built entirely on macOS using [UTM](https://mac.getutm.app/), this lab showcases key security concepts from intrusion detection to network segmentation in a safe, cost-effective, and realistic environment.

---
## 📌 Project Objectives

In cybersecurity, hands-on experience is critical. Employers need candidates who not only understand theoretical concepts, but can also **design, deploy, and defend real systems**. CyberCluster delivers that by:

- 🛠️ Simulating a secure, segmented enterprise network
- 🧪 Supporting offensive and defensive tooling in a virtual environment
- 🧱 Demonstrating working knowledge of firewalls, IDS/IPS, and threat emulation
- 🖥️ Building infrastructure-as-learning: deploy, break, fix, repeat

This project was built to **practice, showcase, and refine** core cybersecurity skills in a way that's portable, repeatable, and fully isolated from production systems.

---

## 💡 Project Core Components

| Component          | Purpose                                      |
|-------------------|----------------------------------------------|
| `pfSense`         | Firewall, Router, DHCP server and Snort IDS host    |
| `Snort`           | Intrusion Detection System (on pfSense)      |
| `Kali Linux`      | Attacker VM for penetration testing          |
| `Metasploitable2` | Vulnerable target machine                    |
| `UTM`             | Virtualization platform (macOS-native)       |

Each machine is configured in a **logically segmented network**, with traffic routed through `pfSense` to enforce visibility, inspection, and defense.

---

## ✅ Skills Demonstrated

| Skill Area             | What You’ll See Here                                    |
|-----------------------|---------------------------------------------------------|
| **Network Security**    | Configured firewall rules, segmented LAN/WAN traffic   |
| **Intrusion Detection** | Monitored network with Snort’s real-time packet inspection |
| **Penetration Testing** | Used Kali Linux to exploit vulnerabilities in Metasploitable2 |
| **Virtualization**      | Managed and configured multiple VMs with UTM on macOS  |
| **Network Architecture**| Set up VLANs, DHCP, NAT, and routing for isolated networks |
| **Documentation & Design** | Created clear, modular guides and structured configs   |


---
## 🌐 Network Design

![Network Topology](https://github.com/tadiusfrank2001/cybercluster/blob/main/cybercluster_topology.png)

To simulate an internal reconnaissance and attack scenario where the Kali Linux attacker machine scans, identifies, and attempts to exploit the Metasploitable2 target, with pfSense (with Snort) logging and potentially blocking malicious activity. All traffic flows through the pfSense firewall, which also acts as the network’s gatekeeper to the internet (WAN).

---

## 🧱 Core Components Configs

This section outlines the core building blocks of the **CyberCluster** lab environment. Each component plays a critical role in simulating a secure and attack-ready network. Click into each module below to explore detailed configuration steps, tools used, and how they contribute to the overall lab architecture.

### 🔐 [pfSense Firewall](./pfSense/README.md)
- Acts as the secure gateway between internal and external networks
- Configured with static LAN IP and DHCP for connected VMs
- WAN uses NAT/shared adapter for controlled internet access
- Firewall rules restrict and monitor traffic between components
- Integrated Snort IDS for packet-level inspection and alerting

### 🎯 [Metasploitable2 (Target VM)](./Metasploitable2/README.md)
- Intentionally vulnerable Linux host for exploitation practice
- Emulates real-world misconfigurations and insecure services
- Part of internal network, assigned static IP via pfSense DHCP
- Ideal for simulating reconnaissance and attack vectors

### 💀 [Kali Linux (Attacker VM)](./KaliLinux/README.md)
- Full-featured offensive security OS for penetration testing
- Connected to the same internal network as the target and firewall
- Tools include Nmap, Metasploit, Burp Suite, etc.
- Used to simulate scanning, exploitation, and lateral movement

### 🛡️ [Snort IDS](./Snort/README.md)
- Deployed on pfSense to inspect internal LAN traffic
- Signature-based detection with custom rule tuning
- Identifies port scans, brute force, and common exploits
- Alerts generated in real-time with optional blocking
