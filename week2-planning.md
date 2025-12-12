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
