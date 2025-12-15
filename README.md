# 💻 CMPN202 Operating Systems Journal

**Student Name:** Bhowan Khawas

**Student ID:** A00028871

This repository contains the technical journal documenting the setup, configuration, security hardening, and performance analysis of a headless Ubuntu Server 24.04 LTS (ARM64) virtual machine, administered remotely from a macOS workstation.

---

## 📚 Journal Contents

### Phase 1: Deployment & Planning
* **[Week 1: System Planning and Distribution Selection](week1.md)**
    * System Architecture Diagram
    * Host & Guest Configuration Justification
    * Network Configuration and CLI Evidence

### Phase 2: Security & Hardening
* **[Week 2: Security Implementation Log](week2.md)**
    * Evidence of System Updates (`apt upgrade`)
    * Firewall Configuration (`ufw`)
    * SSH Public Key Authentication and Password Lockout
* **[Week 2: Security Planning Documents](week2.md)**
    * Security Configuration Checklist
    * Performance Testing Plan
    * Threat Model

### Phase 3: Storage & Performance Planning
* **[Week 3: Storage Configuration and Performance Planning](week3.md)**
    * Logical Volume Management (LVM) Setup Log (PV, VG, LV)
    * Persistent Mount Configuration (`/etc/fstab`)
    * Application Selection Matrix
    * Expected Resource Profiles and Monitoring Strategy

### Phase 4: Testing and Analysis
* **[Week 4: Performance Testing and Analysis](week4.md)**
    * Installation Log & Test Setup
    * CPU, I/O, and Network Stress Testing Results
    * Final Analysis and Security Review

### Phase 5: Final Presentation
* **[Week 5: Video Demonstration and Reflection](week5.md)**
    * Video Presentation Link
    * Critical Reflection and Challenges
    * Final Project Conclusion

### Phase 6: Extended Administration (Future Work)
* **[Week 6: Advanced Configuration (Coming Soon)](week6.md)**
    * *Placeholder: Automation or Containerization Setup*
    * *Placeholder: Advanced Network Services*

### Phase 7: Maintenance & Troubleshooting (Future Work)
* **[Week 7: System Maintenance Log (Coming Soon)](week7.md)**
    * *Placeholder: Log Rotation and Analysis*
    * *Placeholder: Backup and Recovery Strategy*

---

## 🛠️ Infrastructure Overview

| Component | Host / Guest | Details |
| :--- | :--- | :--- |
| **Workstation** | Host (MacBook Pro) | macOS Terminal (ZSH) |
| **Hypervisor** | Host | UTM (QEMU / Apple Hypervisor Framework) |
| **Server OS** | Guest | Ubuntu Server 24.04 LTS (ARM64) |
| **Network** | Shared | Host-Only equivalent (`192.168.64.0/24`) |
