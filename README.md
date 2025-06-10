# 🧠 CyberCluster: A Virtualized Cybersecurity Lab for Real-World Attack & Defense Scenarios

**CyberCluster** is a self-contained, fully virtual cybersecurity lab designed to emulate enterprise-grade attack and defense scenarios using open-source tools and virtualization. Built entirely on macOS using [UTM](https://mac.getutm.app/), this lab showcases key security concepts — from intrusion detection to network segmentation — in a safe, cost-effective, and realistic environment.

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
