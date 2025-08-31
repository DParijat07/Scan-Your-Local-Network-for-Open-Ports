# 🌐 Network Reconnaissance & Port Scan – Case Study

## 🔹 Executive Summary
This project demonstrates a **local network reconnaissance** using **Nmap**.  
The scan was executed on subnet `192.168.0.0/24` to identify active hosts, open ports, and running services.  

📊 **Key Results:**
- **3 hosts discovered** on the network.  
- Exposed services: FTP, HTTP, RPC, SMB, NetBIOS, UPnP, TR-069.  
- Security risks identified: weak router services, SMB exposure, outdated firmware.  

---

## 🔹 Scope & Methodology
- **Target Range:** `192.168.0.0/24`  
- **Techniques Used:**
  - `-sS` → TCP SYN Scan  
  - `-sV` → Version Detection  
  - `-O` → OS Fingerprinting  
  - `-p-` → Full Port Scan  
  - `--min-rate=5000` → Speed optimization  

📂 **Output:** Raw Nmap results saved for analysis.  

---

## 🔹 Findings

### 🖥️ Host 1: D-Link Router (`192.168.0.1`)
- **OS:** Linux Kernel 2.6.23 – 2.6.38  
- **Open Ports:** 21 (FTP), 80 (HTTP), 7547 (TR-069), 32913 (UPnP)  
- **Risks:**
  - UPnP & TR-069 exploited in past router botnets.  
  - Web interface may expose outdated firmware.  
- **Recommendations:**
  - Disable UPnP & TR-069 if not required.  
  - Update firmware.  
  - Restrict access to management ports.  

---

### 💻 Host 2: Windows Machine (`192.168.0.101`)
- **OS:** Likely Microsoft Windows 10/11  
- **Open Ports:** 135 (MSRPC), 139 (NetBIOS), 445 (SMB)  
- **Risks:**
  - SMB/NetBIOS are common ransomware entry points.  
  - RPC may allow user/share enumeration.  
- **Recommendations:**
  - Disable SMBv1 protocol.  
  - Patch Windows OS.  
  - Restrict SMB access to trusted IPs.  

---

### 🔒 Host 3: Unknown Device (`192.168.0.103`)
- **OS:** Unknown  
- **Ports:** All closed (65535 scanned)  
- **Risk:** None (hardened host).  

---

## 🔹 Conclusion
- **High Risk:** D-Link Router (due to UPnP/TR-069 exposure).  
- **Medium Risk:** Windows Device (due to SMB & RPC).  
- **Low Risk:** Hardened Host (no open ports).  

📌 **Mitigation Steps:**
- Disable unnecessary services.  
- Apply firmware & OS security patches.  
- Restrict access using firewalls & ACLs.  

---

## 🔹 Tools Used
- **Nmap** → Reconnaissance & scanning  
- **Wireshark (optional)** → Packet capture validation  
- **Linux Terminal** → Analysis & scripting  

---

## 🔹 Learning Outcomes
- Practical understanding of **Nmap scanning techniques**.  
- Identifying high-risk services in real networks.  
- Writing a **professional vulnerability scan report**.  

---

✅ This project demonstrates a **real-world SOC/VAPT skill**: performing reconnaissance, documenting findings, and providing actionable remediation.  
