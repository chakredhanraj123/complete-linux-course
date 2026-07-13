# Linux System Monitoring

## 📌 Introduction

**System monitoring** is the process of tracking CPU, memory, disk, network, and system performance to ensure a Linux system is running efficiently. It helps administrators identify performance bottlenecks, troubleshoot issues, and maintain system stability.

---

# CPU and Memory Monitoring

Use the following commands to monitor CPU and memory usage.

| Command | Description |
|----------|-------------|
| `top` | Display real-time CPU, memory, and running processes. |
| `htop` | Interactive and user-friendly process viewer (requires installation). |
| `vmstat` | Show CPU, memory, process, and I/O statistics. |
| `free -m` | Display used and available memory in MB. |

Example:

```bash
top
```

```bash
vmstat 1 5
```

```bash
free -m
```

---

# Disk Monitoring

Monitor disk usage and storage availability.

| Command | Description |
|----------|-------------|
| `df -h` | Show disk space usage in a human-readable format. |
| `du -sh /path` | Display the size of a specific directory. |
| `iostat` | Show CPU and disk I/O statistics (requires `sysstat` package). |

Example:

```bash
df -h
```

```bash
du -sh /var/log
```

```bash
iostat
```

---

# Network Monitoring

Monitor network interfaces, connections, and connectivity.

| Command | Description |
|----------|-------------|
| `ip a` | Display IP addresses and network interfaces. |
| `ifconfig` | Display network interface information (deprecated). |
| `ss -tulnp` | Show listening ports and active socket connections. |
| `netstat -tulnp` | Display active connections and listening ports (legacy). |
| `ping hostname` | Test network connectivity. |
| `traceroute hostname` | Display the route packets take to a destination. |
| `nslookup domain` | Check DNS resolution for a domain. |

Example:

```bash
ip a
```

```bash
ss -tulnp
```

```bash
ping google.com
```

---

# Log Monitoring

System logs help identify errors, warnings, and application events.

| Command | Description |
|----------|-------------|
| `tail -f /var/log/syslog` | Monitor log files in real time. |
| `journalctl -f` | View live logs on systemd-based Linux distributions. |
| `dmesg \| tail` | Display the latest kernel log messages. |

Example:

```bash
tail -f /var/log/syslog
```

```bash
journalctl -f
```

```bash
dmesg | tail
```

---

# Common Commands Cheat Sheet

| Command | Purpose |
|----------|---------|
| `top` | Real-time system monitoring |
| `htop` | Interactive process viewer |
| `vmstat` | CPU and memory statistics |
| `free -m` | Check memory usage |
| `df -h` | Check disk space |
| `du -sh /path` | Check directory size |
| `iostat` | Monitor disk I/O |
| `ip a` | View network interfaces |
| `ss -tulnp` | Show listening ports |
| `ping google.com` | Test network connectivity |
| `traceroute google.com` | Trace network path |
| `nslookup example.com` | Verify DNS resolution |
| `tail -f /var/log/syslog` | Monitor logs in real time |
| `journalctl -f` | View live system logs |
| `dmesg \| tail` | Display recent kernel logs |

---

# Best Practices

- Regularly monitor CPU, memory, and disk usage to detect performance issues early.
- Use `top` or `htop` to identify resource-intensive processes.
- Monitor disk usage with `df -h` to prevent storage exhaustion.
- Check network connectivity using `ping` and `ss`.
- Review system and kernel logs regularly for troubleshooting and diagnostics.

---

# Summary

Linux provides powerful built-in tools for monitoring **CPU, memory, disk, network, and system logs**. Commands such as **`top`**, **`free`**, **`df`**, **`ss`**, **`ping`**, and **`journalctl`** are essential for system administrators and DevOps engineers to maintain system health, troubleshoot issues, and optimize performance.
