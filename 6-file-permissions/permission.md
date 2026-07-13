# File Permissions Management in Linux

## 📌 Introduction

Linux uses **file permissions** to control who can **read, write, or execute** files and directories. Proper permission management helps protect system files, user data, and improves overall system security.

Each file and directory has permissions assigned to three categories:

| Category | Description |
|----------|-------------|
| **Owner (User)** | The user who owns the file. |
| **Group** | Users who belong to the assigned group. |
| **Others** | All other users on the system. |

---

# Linux Permission Types

Each permission has both a **symbolic** and **numeric (octal)** value.

| Permission | Symbol | Value | Description |
|------------|--------|-------|-------------|
| Read | `r` | `4` | View the contents of a file or list directory contents. |
| Write | `w` | `2` | Modify or delete a file, or create/delete files in a directory. |
| Execute | `x` | `1` | Execute a script or program, or access a directory. |

---

# Check File Permissions

Use the following command to view file permissions:

```bash
ls -l filename
```

Example:

```bash
-rwxr--r-- 1 user group 1234 Mar 28 10:00 myfile.sh
```

Permission breakdown:

```text
-rwxr--r--

-      → File type
rwx    → Owner permissions
r--    → Group permissions
r--    → Others permissions
```

---

# Changing Permissions with `chmod`

The **chmod** command is used to change file or directory permissions.

## Symbolic Mode

Use symbols to add (`+`), remove (`-`), or set (`=`) permissions.

```bash
chmod u+x filename        # Add execute permission for owner
chmod g-w filename        # Remove write permission from group
chmod o=r filename        # Give read-only permission to others
chmod u=rwx,g=rx,o= filename
```

---

## Numeric (Octal) Mode

Permission values:

- Read = **4**
- Write = **2**
- Execute = **1**

Common examples:

```bash
chmod 755 filename
chmod 644 filename
chmod 700 filename
```

| Permission | Meaning |
|------------|---------|
| `755` | Owner: `rwx`, Group: `r-x`, Others: `r-x` |
| `644` | Owner: `rw-`, Group: `r--`, Others: `r--` |
| `700` | Owner: `rwx`, Group/Others: No access |

---

# Changing Ownership with `chown`

The **chown** command changes the owner or group of a file.

```bash
chown newuser filename
chown newuser:newgroup filename
chown :newgroup filename
```

Change ownership recursively:

```bash
chown -R newuser:newgroup directory/
```

---

# Changing Group with `chgrp`

Use **chgrp** to change the group ownership.

```bash
chgrp newgroup filename
```

Recursive example:

```bash
chgrp -R newgroup directory/
```

---

# Special Permissions

Linux provides three special permissions for advanced access control.

## SetUID (SUID)

Runs a program with the **owner's permissions**.

```bash
chmod u+s filename
```

Example:

```text
/usr/bin/passwd
```

---

## SetGID (SGID)

- **Files:** Execute with the group's permissions.
- **Directories:** Newly created files inherit the directory's group.

```bash
chmod g+s filename
chmod g+s directory/
```

---

## Sticky Bit

Allows only the **file owner** (or root) to delete files inside a shared directory.

```bash
chmod +t directory/
```

Example:

```text
/tmp
```

---

# Default Permissions with `umask`

The **umask** command defines the default permissions for newly created files and directories.

Check the current umask:

```bash
umask
```

Set a new umask:

```bash
umask 022
```

Typical defaults:

| Item | Default Permission |
|------|--------------------|
| Directory | `755` |
| File | `644` |

---

# Common Commands Cheat Sheet

| Command | Description |
|----------|-------------|
| `ls -l` | View file permissions |
| `chmod 755 file` | Change file permissions |
| `chmod u+x file` | Add execute permission to owner |
| `chown user file` | Change file owner |
| `chown user:group file` | Change owner and group |
| `chgrp group file` | Change group ownership |
| `chmod u+s file` | Set SetUID permission |
| `chmod g+s dir` | Set SetGID permission |
| `chmod +t dir` | Set Sticky Bit |
| `umask` | Display default permission mask |

---

# Best Practices

- Follow the **Principle of Least Privilege**—grant only the permissions required.
- Avoid using `777` unless absolutely necessary.
- Use **644** for regular files and **755** for executable files and directories.
- Regularly review ownership and permissions of sensitive files.
- Use special permissions (SUID, SGID, Sticky Bit) only when required.

---

# Summary

Linux file permissions are a fundamental security feature that controls access to files and directories. Using commands like **`chmod`**, **`chown`**, **`chgrp`**, and **`umask`**, administrators can securely manage permissions, ownership, and default access settings for users and groups.
