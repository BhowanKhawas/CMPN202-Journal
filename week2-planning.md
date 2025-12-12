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

## 1. Performance Testing Plan (To be written next)

*Placeholder for Deliverable 1*

## 3. Threat Model (To be written next)

*Placeholder for Deliverable 3*



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
