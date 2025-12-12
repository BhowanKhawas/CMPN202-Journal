# Week 3: Storage Configuration and Performance Planning

## 1. Storage Configuration Log (LVM Implementation)
This section documents the creation of a flexible, independent 4GB storage partition using Logical Volume Management (LVM) for future data and test applications.

| Command/Action | Purpose | Status |
| :--- | :--- | :--- |
| **Hardware Setup** | Added a new 4GB virtual disk (`/dev/vdb`) via UTM settings. | COMPLETE |
| `sudo pvcreate /dev/vdb` | Initialized the disk as a Physical Volume (PV). | COMPLETE |
| `sudo vgcreate vg_data /dev/vdb` | Created a Volume Group (VG) to pool the disk space. | COMPLETE |
| `sudo lvcreate -l 100%FREE -n lv_storage vg_data` | Created the Logical Volume (LV) using all available space. | COMPLETE |
| :--- | :--- | :--- |
**Evidence:** Logical Volume Structure (`vgs` and `lvs`)
![LVM Structure](LVM.png) 
| :--- | :--- | :--- |
| `sudo mkfs.ext4 /dev/mapper/vg_data-lv_storage` | Formatted the LV with the ext4 filesystem. | COMPLETE |
| `sudo mkdir /mnt/storage` | Created the mount point. | COMPLETE |
| `sudo mount ... /mnt/storage` | Mounted the new partition. | COMPLETE |
| **Persistence** | Updated `/etc/fstab` with the UUID to ensure the LV remounts on reboot. | COMPLETE |
| :--- | :--- | :--- |
**Evidence:** Final Persistent Mount Verification (`df -h` after reboot)
![Final Mount Verification](mounted.png)

---

## 2. Application Selection Matrix (Deliverable 1)

This matrix selects applications representing distinct workload types for performance evaluation in Week 4.

| Workload Type | Application | Justification |
| :--- | :--- | :--- |
| **CPU-Intensive** | **`stress-ng`** | Applies configurable synthetic load across all cores to measure maximum CPU throughput and core stability. |
| **RAM-Intensive** | **`stress-ng`** | Configured to allocate and dirty large amounts of memory, testing memory controller and swap performance. |
| **I/O-Intensive** | **`fio` (Flexible I/O Tester)** | Industry-standard tool for generating custom block-level disk reads and writes, ideal for testing the new LVM partition (`/mnt/storage`). |
| **Network-Intensive** | **`iperf3`** | Dual-mode client/server tool used to generate and measure network bandwidth and latency between the Host and the Guest. |
| **Server Application** | **`NGINX`** | A lightweight but common web server used to simulate a production workload and measure stability and response time under modest load. |

---

## 3. Expected Resource Profiles (Deliverable 3)

Anticipated resource usage during the performance tests for proper analysis.

* **`stress-ng` (CPU):** Expected CPU utilization near **100%** on all allocated cores. RAM usage remains low.
* **`stress-ng` (RAM):** Expected RAM utilization near **100%** (filling both physical memory and swap); CPU utilization should be moderate (20-40%).
* **`fio` (I/O):** Expected Disk I/O (reads/writes) to be near maximum throughput on the LVM partition; CPU and RAM usage should be low/moderate.
* **`iperf3` (Network):** Expected minimal CPU or RAM usage, but high network interface utilization; performance is dependent on the virtual network bridge speed.

---

## 4. Monitoring Strategy (Deliverable 4)

This explains the specific commands and approach used to measure performance remotely.

| Metric | Server Command | Host Command | Purpose |
| :--- | :--- | :--- | :--- |
| **CPU/RAM Load** | `top` / `free -h` | N/A | Real-time monitoring of CPU core usage and memory consumption on the server. |
| **Disk I/O** | `iostat` | N/A | Measures throughput (MB/s) and latency on the `/dev/mapper/vg_data-lv_storage` partition during `fio` tests. |
| **Network Latency**| N/A | `ping 192.168.64.8` | Captures Round-Trip Time (RTT) delay and packet loss from the host workstation during high-stress tests. |
| **Process State** | `ps aux` | N/A | Verifies that the test application (`stress-ng`, `fio`, etc.) is running correctly and consuming the expected resources. |
