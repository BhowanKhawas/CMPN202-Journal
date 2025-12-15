# Week 5: Final Presentation and Reflection

## 1. Video Presentation
This video demonstrates the successful deployment, security hardening, storage configuration, and performance testing of the Ubuntu Server.

* **Video Link:** [Watch Demonstration Video](BhowanKhawas_OSCoursework_Demonstration.mp4)
* **Duration:** 8:30 minutes  **Demonstration Highlights:**
* System Architecture and SSH Access
* UFW Firewall Status and Rules
* LVM Storage Structure and Persistence
* Live Performance Testing (CPU, Disk I/O, Network)

---

## 2. Critical Reflection

### What Went Well
* **Virtualization:** Deploying the Ubuntu Server on UTM (Apple Silicon) was smooth, and the bridge network configuration allowed for seamless communication between the Host and Guest.
* **Automation:** Using `ssh-copy-id` and scripts for installation saved significant time during the setup process.
* **Performance:** The server handled the `stress-ng` CPU loads effectively, proving the stability of the virtualised environment.

### Challenges Faced
* **LVM Permissions:** Initially, the `fio` test failed because the non-root user did not have write permissions to `/mnt/storage`. This was resolved by changing directory ownership using `chown`.
* **Network Testing:** Running `iperf3` required troubleshooting the firewall (UFW) to explicitly allow port 5201, which was blocking the connection by default.

---

## 3. Final Project Conclusion
This project successfully delivered a hardened, production-ready Linux server. The system meets all functional requirements for remote administration, secure storage management, and high-performance throughput, as evidenced by the technical journal and performance logs.
