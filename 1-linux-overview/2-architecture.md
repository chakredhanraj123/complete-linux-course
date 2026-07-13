# Objective

After completing this chapter, you will understand:

- What are the core components of a Linux machine
- How Linux is structured internally
- How a command travels from the user to the hardware
- Difference between Kernel, Shell, Libraries and Applications
- Why understanding Linux architecture is important for DevOps Engineers

---

# What is Linux Structure?

Linux follows a **layered architecture**, where each layer has a specific responsibility.

Instead of applications directly communicating with hardware, every request goes through the Linux kernel.

This design makes Linux:

- Stable
- Secure
- Fast
- Modular
- Easy to maintain

---

# Linux Architecture Diagram

```
+--------------------------------------------------------------------+
|                     User Applications                              |
|--------------------------------------------------------------------|
|  Vim | Nano | Docker | Git | Nginx | Apache | Python | Java | kubectl |
+--------------------------------------------------------------------+
|                        Shell                                       |
|--------------------------------------------------------------------|
|      Bash | Zsh | Fish | Ksh | Dash | Tcsh                         |
+--------------------------------------------------------------------+
|                    System Libraries                                |
|--------------------------------------------------------------------|
| glibc | libc | OpenSSL | pthread | libstdc++ | zlib               |
+--------------------------------------------------------------------+
|                    System Utilities                                |
|--------------------------------------------------------------------|
| ls | cp | mv | grep | find | ps | top | systemctl | ip | ssh       |
+--------------------------------------------------------------------+
|                     Linux Kernel                                   |
|--------------------------------------------------------------------|
| Process | Memory | Scheduler | Device Drivers | Filesystem | Network|
+--------------------------------------------------------------------+
|                      Hardware                                      |
|--------------------------------------------------------------------|
| CPU | RAM | SSD/HDD | NIC | Keyboard | Mouse | GPU | USB Devices   |
+--------------------------------------------------------------------+
```

---

# Linux Architecture (Simple View)

```
                User
                  │
                  ▼
        User Applications
                  │
                  ▼
              Shell
                  │
                  ▼
         System Libraries
                  │
                  ▼
           Linux Kernel
                  │
                  ▼
              Hardware
```

Every command ultimately reaches the **Kernel**, because only the kernel has permission to communicate directly with hardware.

---

# Components of Linux Architecture

---

# 1. Hardware Layer

The hardware layer consists of all the physical devices connected to the computer.

Examples

- CPU
- RAM
- Hard Disk / SSD
- Network Card
- Keyboard
- Mouse
- GPU
- USB Devices
- Printer
---

# 2. Linux Kernel

The Kernel is the heart of Linux.
Everything depends on the kernel.
Without the kernel,
Linux cannot boot.

---

## Responsibilities of Kernel

The kernel manages:

- CPU
- RAM
- Processes
- Files
- Network
- Hardware
- Security

Think of the kernel as the **manager of the entire operating system**.

---

# Kernel Responsibilities Diagram

```
               Linux Kernel
                     │
 ┌───────────────────┼────────────────────┐
 │                   │                    │
 ▼                   ▼                    ▼
CPU              Memory               Storage

 ▼                   ▼                    ▼
Processes      Virtual Memory        File System

 ▼
Networking

 ▼
Device Drivers
```
---

# 3. Shell

The Shell is a command interpreter.
It accepts commands from users and communicates with the kernel.
Without a shell,
Users cannot easily interact with Linux.

---

# 4. System Libraries

Applications do not directly talk to the kernel.
Instead,
they use libraries.

Example
```
Application
↓
glibc
↓
Kernel
↓
Hardware
```
---

# 5. System Utilities

Utilities are built-in Linux tools.

Examples
```
ls
cp
mv
rm
find
grep
awk
sed
ps
kill
systemctl
journalctl
ip
ssh
tar
gzip
```
---

# 6. User Applications

These are software used by users.

Examples
- Docker
- Git
- VS Code
- Firefox
- Chrome
- Python
- Java
- Nginx
- Apache
- MySQL
- Kubernetes CLI

Applications rely on libraries and the kernel for all hardware access.

---
