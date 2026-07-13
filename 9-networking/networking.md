# Linux Networking Commands

## 📌 Introduction

Networking commands in Linux are used to **check network connectivity, view IP addresses, troubleshoot network issues, monitor open ports, and download data from the internet**. These commands are essential for Linux administrators, DevOps engineers, and system administrators.

---

# Common Networking Commands

| Command | Description |
|----------|-------------|
| `ping google.com` | Check connectivity to a remote host and measure network latency. |
| `ifconfig` | Display network interface information (**deprecated**, use `ip` command instead). |
| `ip a` | Display IP addresses and network interface details. |
| `netstat -tulnp` | Show active network connections and listening ports (legacy command). |
| `curl https://example.com` | Retrieve data from a URL or test web APIs. |
| `wget https://example.com/file.zip` | Download files from the internet. |

---

# Command Examples

## Check Network Connectivity

```bash
ping google.com
```

Tests whether a remote host is reachable and displays response time.

---

## View Network Interfaces

```bash
ip a
```

Displays IP addresses, network interfaces, and interface status.

> **Note:** `ifconfig` is deprecated on most modern Linux distributions. Use `ip a` instead.

---

## View Open Ports

```bash
netstat -tulnp
```

Displays active network connections and listening TCP/UDP ports.

> Modern Linux systems recommend using:

```bash
ss -tulnp
```

---

## Retrieve Data from a Website

```bash
curl https://example.com
```

Common uses:

- Test REST APIs
- Fetch web page content
- Verify web server responses

---

## Download Files

```bash
wget https://example.com/file.zip
```

Downloads files directly from the internet and supports resuming interrupted downloads.

---

# Common Commands Cheat Sheet

| Command | Purpose |
|----------|---------|
| `ping google.com` | Test network connectivity |
| `ip a` | View IP addresses and interfaces |
| `ifconfig` | Display interface information (legacy) |
| `netstat -tulnp` | Show open ports and network connections |
| `ss -tulnp` | Modern alternative to `netstat` |
| `curl URL` | Retrieve web content or test APIs |
| `wget URL` | Download files from the internet |

---

# Best Practices

- Use `ip a` instead of the deprecated `ifconfig`.
- Use `ss` instead of `netstat` on modern Linux distributions.
- Use `ping` to verify network connectivity before troubleshooting applications.
- Use `curl` for API testing and HTTP request debugging.
- Use `wget` to download software packages, scripts, or backups.

---

# Summary

Linux networking commands help administrators **verify connectivity, inspect network interfaces, monitor open ports, test web services, and download files**. Mastering commands such as **`ping`**, **`ip`**, **`ss`**, **`curl`**, and **`wget`** is an essential skill for Linux, Networking, and DevOps professionals.
