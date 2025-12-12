# Week 4: Performance Testing and Analysis

This phase executes the performance testing plan established in Week 3, utilising the `stress-ng`, `fio`, and `iperf3` utilities to benchmark the server under different workload conditions.

## 1. Test Setup and Installation Log

Before testing, the necessary utilities were installed on the server via SSH.

```bash
# Install performance testing tools and web server
sudo apt update
sudo apt install -y stress-ng fio iperf3 nginx
