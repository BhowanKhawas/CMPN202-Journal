# Week 4: Performance Testing and Analysis

This phase executes the performance testing plan established in Week 3, utilising the `stress-ng`, `fio`, and `iperf3` utilities to benchmark the server under different workload conditions.

## 1. Test Setup and Installation Log

Before testing, the necessary utilities were installed on the server via SSH. The verification below confirms all required tools are present.

```bash
# Verify installation of performance testing tools
apt list --installed | grep -E "(stress-ng|fio|iperf3|nginx)"

## 2\. Performance Testing Execution and Results

All tests were performed remotely from the Host Workstation via SSH.

### A. CPU-Intensive Workload (`stress-ng`)

**Objective:** Measure maximum CPU throughput and core stability.
**Command:** `stress-ng --cpu 4 --timeout 60s`

| Metric | Result | Observation |
| :--- | :--- | :--- |
| **CPU Utilization** | \~98-100% | CPU cores were fully saturated. |
| **Status** | Passed | The test completed successfully without crashing the system. |

### B. I/O-Intensive Workload (`fio`)

**Objective:** Test the read/write performance of the new LVM partition (`/mnt/storage`).
**Preparation:** Permissions were adjusted to allow the non-root user to write to the mount point (`sudo chown -R bhowan:bhowan /mnt/storage`).

**Command:** `fio --name=randwrite --ioengine=libaio ... --directory=/mnt/storage`

| Metric | Result | Analysis |
| :--- | :--- | :--- |
| **Throughput (Write)** | **417 MiB/s** | Extremely high throughput for a virtualized disk. |
| **IOPS** | **107k** | Indicates the VirtIO driver is functioning efficiently with low overhead. |

### C. Network-Intensive Workload (`iperf3`)

**Objective:** Measure maximum bandwidth between the Host (Mac) and Guest (Ubuntu).
**Procedure:** `iperf3 -s` was run on the server, and `iperf3 -c 192.168.64.8` was executed from the Mac terminal.

| Metric | Result | Analysis |
| :--- | :--- | :--- |
| **Bandwidth (Host -\> Guest)** | **4.04 Gbits/sec** | Validates that the virtual network bridge supports gigabit-class speeds suitable for production workloads. |
| **Transfer Volume** | 4.70 GBytes | Transferred nearly 5GB of data in 10 seconds with no connection drops. |

-----

## 3\. Conclusion and Security Review

The performance tests confirm that the server is stable under extreme load across CPU, I/O, and Network resources.

  * **CPU:** Handled 100% load across 4 cores.
  * **Storage:** The LVM partition provides high-speed access (\>400 MB/s) for data storage.
  * **Network:** The connection is stable and capable of high-speed transfers (\>4 Gbps).

-----

## 4\. Final Project Completion Summary

This section confirms that all deliverables for Weeks 1 through 4 have been completed and documented.

| Phase | Week | Deliverable | Status | Key Evidence |
| :--- | :--- | :--- | :--- | :--- |
| **Deployment** | 1 | System Architecture & Network Config | **COMPLETE** | `ip a` screenshot, Arch Diagram |
| **Security** | 2 | System Updates & Firewall (UFW) | **COMPLETE** | `ufw status` screenshot |
| | 2 | SSH Hardening (Key Auth & Lockout) | **COMPLETE** | `ssh-copy-id` & Login screenshots |
| **Storage** | 3 | LVM Implementation (PV/VG/LV) | **COMPLETE** | `vgs`/`lvs` screenshots |
| | 3 | Persistent Mounting (/etc/fstab) | **COMPLETE** | `df -h` screenshot (after reboot) |
| **Testing** | 4 | Performance Benchmarking | **COMPLETE** | `fio` and `iperf3` results |

```
```
