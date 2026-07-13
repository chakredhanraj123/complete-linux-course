# Disk and Storage Management in Linux

## 📌 Introduction

Disk and Storage Management in Linux involves **viewing disks, creating partitions, formatting file systems, mounting storage, managing Logical Volumes (LVM), and configuring swap space**. These tasks are essential for managing storage efficiently and ensuring system reliability.

---

# View Disk Information

Use the following commands to check available disks, partitions, and storage usage.

| Command | Description |
|----------|-------------|
| `lsblk` | Display all block devices and partitions. |
| `fdisk -l` | List all disk partitions. |
| `blkid` | Display UUID and filesystem information. |
| `df -h` | Show disk space usage in a human-readable format. |
| `du -sh /path` | Display the size of a directory. |

Example:

```bash
lsblk
df -h
du -sh /var/log
```

---

# Partition Management

Create and manage disk partitions.

| Command | Description |
|----------|-------------|
| `fdisk /dev/sdX` | Create or modify MBR partitions. |
| `parted /dev/sdX` | Manage GPT partitions. |
| `mkfs.ext4 /dev/sdX1` | Format a partition with the ext4 filesystem. |
| `mkfs.xfs /dev/sdX1` | Format a partition with the XFS filesystem. |

Example:

```bash
sudo fdisk /dev/sdb
sudo mkfs.ext4 /dev/sdb1
```

---

# Mounting and Unmounting

Mount a filesystem to make it accessible.

| Command | Description |
|----------|-------------|
| `mount /dev/sdX1 /mnt` | Mount a partition. |
| `umount /mnt` | Unmount a partition. |
| `mount -o remount,rw /mnt` | Remount a filesystem as read-write. |

Example:

```bash
sudo mount /dev/sdb1 /data
sudo umount /data
```

---

# Logical Volume Management (LVM)

LVM provides flexible disk management by creating logical storage volumes.

| Command | Description |
|----------|-------------|
| `pvcreate /dev/sdX` | Create a Physical Volume (PV). |
| `vgcreate vg_name /dev/sdX` | Create a Volume Group (VG). |
| `lvcreate -L 10G -n lv_name vg_name` | Create a Logical Volume (LV). |
| `mkfs.ext4 /dev/vg_name/lv_name` | Format the logical volume. |
| `mount /dev/vg_name/lv_name /mnt` | Mount the logical volume. |

---

# Swap Management

Swap space acts as virtual memory when physical RAM is exhausted.

| Command | Description |
|----------|-------------|
| `mkswap /dev/sdX` | Create a swap partition. |
| `swapon /dev/sdX` | Enable swap space. |
| `swapoff /dev/sdX` | Disable swap space. |

Example:

```bash
sudo mkswap /dev/sdb2
sudo swapon /dev/sdb2
```

---

# When to Use Each Command

## View Available Disks

```bash
lsblk
```

Use this command to identify available disks and partitions before performing any storage operations.

---

## Use `fdisk`

Use `fdisk` when:

- A new disk has no partitions.
- You need to create or modify disk partitions.

```bash
sudo fdisk /dev/sdb
```

---

## Use `mount`

Use `mount` when:

- A partition already exists.
- The partition is formatted.
- You want to access the filesystem.

```bash
sudo mount /dev/sdb1 /data
```

---

## Full Setup for a New Disk

For a brand-new disk:

```bash
# View available disks
lsblk

# Create a partition
sudo fdisk /dev/sdb

# Format the partition
sudo mkfs.ext4 /dev/sdb1

# Create a mount point
sudo mkdir /data

# Mount the partition
sudo mount /dev/sdb1 /data
```

---

# Common Commands Cheat Sheet

| Command | Purpose |
|----------|---------|
| `lsblk` | View disks and partitions |
| `fdisk -l` | List partition details |
| `blkid` | Show UUID and filesystem type |
| `df -h` | Check disk space usage |
| `du -sh /path` | Check directory size |
| `fdisk /dev/sdX` | Create or edit partitions |
| `mkfs.ext4 /dev/sdX1` | Format partition as ext4 |
| `mount /dev/sdX1 /mnt` | Mount a partition |
| `umount /mnt` | Unmount a partition |
| `pvcreate` | Create Physical Volume |
| `vgcreate` | Create Volume Group |
| `lvcreate` | Create Logical Volume |
| `mkswap` | Create swap space |
| `swapon` | Enable swap |
| `swapoff` | Disable swap |

---

# Best Practices

- Use `lsblk` before modifying disks to identify the correct device.
- Format new partitions before mounting them.
- Avoid modifying mounted partitions unless necessary.
- Use LVM for flexible storage management in servers.
- Configure permanent mounts using `/etc/fstab`.
- Regularly monitor disk usage with `df -h` and `du`.

---

# Summary

Linux provides powerful tools for managing storage, including **partitioning (`fdisk`)**, **formatting (`mkfs`)**, **mounting (`mount`)**, **Logical Volume Management (LVM)**, and **swap management**. Understanding these commands is essential for Linux administrators, system engineers, and DevOps professionals managing servers and storage infrastructure.
