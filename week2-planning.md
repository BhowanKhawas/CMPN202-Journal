# Phase 2 Planning Documents

## 2. Security Configuration Checklist

The following checklist verifies the security baseline established on the Ubuntu Server 24.04 LTS (ARM64) remote administration platform.

| Security Area | Configuration Item | Status | Verification (CLI/File) |
| :--- | :--- | :--- | :--- |
| **I. Access Control** | | | |
| SSH Hardening | Public Key Authentication enabled | ✅ DONE | Tested successful key login (`ssh.png`) |
| SSH Hardening | Password login completely disabled | ✅ DONE | Tested lockout (`lockout.png`) |
| User Management | Primary user granted `sudo` privilege | ✅ DONE | Initial server setup |
| **II. Network Perimeter** | | | |
| Firewall (UFW) | Default inbound policy set to DENY | ✅ DONE | `sudo ufw status verbose` |
| Firewall (UFW) | Port 22 (SSH) explicitly ALLOWED | ✅ DONE | `sudo ufw status verbose` |
| **III. System Maintenance**| | | |
| Patching | System packages updated to latest version | ✅ DONE | `sudo apt upgrade -y` |
| Maintenance | Automatic updates configured (Default) | ✅ DONE | Ubuntu Server 24.04 LTS Default |

---

## 1. Performance Testing Plan

The goal of this plan is to establish a performance baseline for the headless server under specific load conditions and to verify the stability of the remote SSH administration channel.

### Methodology and Tools
1.  **Load Generation Tool:** The open-source `stress-ng` utility will be used on the Ubuntu Server to apply a defined, measurable load on the CPU and RAM.
2.  **Monitoring Tools:**
    * **Host (MacBook Pro):** The local terminal will be used to run the `ping` command to monitor network latency and packet loss to the server under load.
    * **Server (Ubuntu):** The `top` and `free` commands will be run concurrently in a separate SSH session to monitor CPU utilisation and memory consumption in real-time.
3.  **Metrics to Capture:**
    * **CPU Utilisation:** Percentage of time the CPU cores are busy during the test.
    * **System Load:** The average number of processes waiting for CPU time.
    * **Network Latency (RTT):** The Round-Trip Time (RTT) delay is measured in milliseconds (ms) between the Mac and the server.

### Test Procedure
The test will be conducted over two SSH sessions running simultaneously from the MacBook Pro Workstation:

1.  **Session 1 (Monitoring):** Run `ping 192.168.64.8` to continuously measure network latency.
2.  **Session 2 (Load Generation):** Run `stress-ng --cpu 4 --timeout 300s` to place 4 processes under heavy load for 5 minutes (300 seconds).
3.  **Data Capture:** Record the average RTT from the `ping` test and the maximum CPU load from the `top` utility while the test is active.

4.  ## 3. Threat Model

This threat model identifies three primary attack vectors applicable to a headless virtual server deployed in a shared-network environment and details the implemented mitigation strategies.

| Threat | Description | Implemented Mitigation Strategy |
| :--- | :--- | :--- |
| **1. Brute-Force Attack** | An automated script attempting to guess the user's password repeatedly via the SSH login prompt. | **SSH Hardening (PKI):** Password authentication was completely disabled in the SSH configuration (`PasswordAuthentication no`). The server will not accept any password-based login attempt, rendering brute-force attacks ineffective and blocking the primary attack vector. |
| **2. Unauthorized External Access** | Attempts by external devices on the local area network (LAN) or the internet to scan and access unnecessary services (e.g., ports 80, 443, 21, etc.). | **Perimeter Firewall (UFW):** The Uncomplicated Firewall (UFW) was configured to have a default inbound policy of **DENY**. The only exception is TCP Port 22, which is explicitly allowed for SSH access. All other ports are invisible and blocked. |
| **3. Privilege Escalation / Unpatched Vulnerabilities** | An attacker (or malware) exploiting known security bugs in outdated software (like the kernel, OpenSSH, or web server) to gain root access. | **Routine Patching:** The system was fully updated using `sudo apt upgrade -y` immediately after installation. This ensures all known vulnerabilities are patched, reducing the attack surface. An eventual policy for automatic daily updates will be implemented to sustain this defense. |

---

### **Final Week 2 Summary**

You have now completed the documentation for **all three deliverables** of Phase 2 (Security Planning):

1.  **[x] Performance Testing Plan**
2.  **[x] Security Configuration Checklist**
3.  **[x] Threat Model**

**You are completely finished with the work for Week 2!**

Please save your file by clicking **Commit changes** on GitHub. You can now relax and prepare for Week 3.
