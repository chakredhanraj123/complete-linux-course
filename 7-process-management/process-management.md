# Process Management in Linux

## 📌 Introduction

A **process** is an instance of a running program. Every process in Linux has a unique **Process ID (PID)** and is managed by the operating system. Linux provides several commands to view, monitor, control, and terminate processes.

---

# Viewing Processes

Use the following commands to display running processes.

| Command | Description |
|----------|-------------|
| `ps aux` | Display all running processes. |
| `ps -u username` | Show processes owned by a specific user. |
| `ps -C processname` | Display a process by its name. |
| `pgrep processname` | Find the PID of a process by name. |
| `pidof processname` | Display the PID of a running program. |

---

# Managing Processes

Use these commands to stop, resume, or terminate processes.

| Command | Description |
|----------|-------------|
| `kill PID` | Gracefully terminate a process using its PID. |
| `kill -9 PID` | Forcefully kill a process. |
| `pkill processname` | Kill a process using its name. |
| `pkill -9 processname` | Forcefully kill all matching processes. |
| `kill -STOP PID` | Pause (stop) a running process. |
| `kill -CONT PID` | Resume a paused process. |

---

# Process Priority

Linux assigns a priority (Nice value) to every process.

| Command | Description |
|----------|-------------|
| `nice -n 10 command` | Start a process with lower priority. |
| `renice -n 10 -p PID` | Lower the priority of an existing process. |
| `renice -n -5 -p PID` | Increase the priority (requires root privileges). |

> **Note:** Lower Nice value = Higher priority, Higher Nice value = Lower priority.

---

# Background and Foreground Processes

Run and manage commands in the background.

| Command | Description |
|----------|-------------|
| `command &` | Run a command in the background. |
| `jobs` | Display background jobs. |
| `fg %jobnumber` | Bring a background job to the foreground. |
| `Ctrl + Z` | Suspend the current running process. |
| `bg %jobnumber` | Resume a suspended process in the background. |

---

# Monitoring Processes

Monitor system resource usage and running processes.

| Command | Description |
|----------|-------------|
| `top` | Interactive real-time process monitor. |
| `htop` | User-friendly process monitor (install separately). |

Useful keys in `top`:

- `k` → Kill a process
- `r` → Change process priority (Renice)
- `q` → Quit

---

# Managing Services (Daemon Processes)

A **daemon** is a background service that starts automatically or runs continuously.

| Command | Description |
|----------|-------------|
| `systemctl list-units --type=service` | List all running services. |
| `systemctl start service-name` | Start a service. |
| `systemctl stop service-name` | Stop a service. |
| `systemctl restart service-name` | Restart a service. |
| `systemctl status service-name` | Check service status. |
| `systemctl enable service-name` | Enable a service at boot. |
| `systemctl disable service-name` | Disable a service at boot. |

---

# Common Commands Cheat Sheet

| Command | Purpose |
|----------|---------|
| `ps aux` | View all running processes |
| `pgrep nginx` | Find PID by process name |
| `pidof sshd` | Get PID of a running program |
| `kill PID` | Terminate a process |
| `kill -9 PID` | Force kill a process |
| `pkill processname` | Kill process by name |
| `top` | Monitor system processes |
| `htop` | Advanced process viewer |
| `jobs` | List background jobs |
| `fg %1` | Bring job to foreground |
| `bg %1` | Resume job in background |
| `nice -n 10 command` | Start with lower priority |
| `renice -n 5 -p PID` | Change process priority |
| `systemctl status nginx` | Check service status |

---

# Best Practices

- Use `ps`, `pgrep`, or `pidof` to identify the correct process before terminating it.
- Use `kill` before `kill -9`; force kill only when necessary.
- Monitor system performance regularly with `top` or `htop`.
- Use `systemctl` to manage services instead of manually killing daemon processes.
- Adjust process priorities using `nice` and `renice` to optimize system performance.

---

# Summary

Linux process management allows administrators to efficiently monitor, control, and troubleshoot running programs. Commands such as **`ps`**, **`top`**, **`kill`**, **`pgrep`**, **`nice`**, **`renice`**, and **`systemctl`** are essential tools for managing processes and services in any Linux environment.
