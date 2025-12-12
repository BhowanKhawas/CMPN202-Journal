# 💻 CMPN202 Operating Systems Journal

Student Name: Bhowan Khawas

Student ID: A00028871

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
* **[Week 2: Security Planning Documents](week2-planning.md)**
    * Security Configuration Checklist
    * Performance Testing Plan
    * Threat Model

### Phase 3: Storage & Performance Planning
* **[Week 3: Storage Configuration and Performance Planning](week3.md)**
    * Logical Volume Management (LVM) Setup Log (PV, VG, LV)
    * Persistent Mount Configuration (/etc/fstab)
    * Application Selection Matrix
    * Expected Resource Profiles and Monitoring Strategy
  
### Phase 4: Testing and Analysis
* **[Week 3: Performance Testing and Analysis](week4.md)**

### Future Phases (Coming Soon)
---

## 🛠️ Infrastructure Overview

| Component | Host / Guest | Details |
| :--- | :--- | :--- |
| **Workstation** | Host (MacBook Pro) | macOS Terminal (ZSH) |
| **Hypervisor** | Host | UTM (QEMU / Apple Hypervisor Framework) |
| **Server OS** | Guest | Ubuntu Server 24.04 LTS (ARM64) |
| **Network** | Shared | Host-Only equivalent (192.168.64.0/24) |
