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
- (Optional) Convert for UTM compatibility:

  ```bash
  qemu-img convert -f vmdk -O qcow2 input.vmdk output.qcow2
  ```
