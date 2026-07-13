# User Management in Linux

> **Linux User Management**
>
> This module explains how Linux manages users and groups, how authentication works, password management, privilege escalation, sudo access, and security best practices.
>
> **Target Audience:** Beginners to DevOps Engineers
>
> **Prerequisites**
> - Basic Linux Commands
> - File System Knowledge
> - Terminal Basics

---

# What You Will Learn

After completing this module you will understand:

- What is a Linux user
- Why Linux is called a Multi-user Operating System
- Types of users
- UID and GID
- User Database Files
- Group Management
- Password Management
- User Creation
- User Modification
- User Deletion
- Sudo Access
- Password Policies
- Security Best Practices

---

# Real World Scenario

Imagine your company has:

- 500 Developers
- 100 QA Engineers
- 50 DevOps Engineers
- 20 Database Administrators
- 10 Security Engineers

Can everyone use the same account?

**Absolutely NOT.**

Each person receives:

- Personal Username
- Personal Password
- Different Permissions
- Different Groups
- Different Home Directory

This is called **User Management**.

---

# Why User Management is Important

Without user management,

- Anyone could delete files
- Anyone could shutdown the server
- Anyone could install malware
- No audit logs
- No accountability

User management provides

- Authentication
- Authorization
- Accountability
- Security
- Auditability

---

# Linux is a Multi-user Operating System

Unlike Windows Home editions, Linux was designed from the beginning for multiple users.

Example

```
Server

├── Dhanraj
├── Rahul
├── Priya
├── Amit
├── DevOps
├── Jenkins
├── GitLab
├── MySQL
└── Apache
```

Notice something interesting.

Not only humans...

Applications also run as users.

Example

```
mysql
nginx
apache
nobody
jenkins
gitlab
postgres
```

Every process in Linux belongs to a user.

---

# Authentication Flow

```
          Login

             │

             ▼

      Username + Password

             │

             ▼

      /etc/passwd

             │

             ▼

      /etc/shadow

             │

             ▼

 Password Verified?

      Yes         No

       │           │

       ▼           ▼

   Login       Access Denied
```

---

# Types of Users

Linux mainly has three user types.

---

## 1. Root User

The most powerful account.

Username

```
root
```

UID

```
0
```

Can

- Install software
- Delete users
- Shutdown system
- Modify kernel
- Manage disks
- Change permissions
- Access every file

Example

```
sudo su -

whoami

root
```

---

## 2. Regular Users

These are human users.

Example

```
rahul
amit
john
developer
```

Usually

UID starts from

```
1000
```

They have

- Home directory
- Personal files
- Limited permissions

Example

```
/home/rahul

/home/amit
```

---

## 3. System Users

Created automatically during package installation.

Example

```
mysql
nginx
apache
daemon
bin
mail
nobody
```

Purpose

Applications run using these accounts.

Why?

Security.

If Apache gets hacked,

only Apache permissions are compromised.

Not the whole system.

---

# UID (User ID)

Every Linux user has a unique number.

Example

```
root

UID = 0
```

```
rahul

UID = 1001
```

Check UID

```
id username
```

Example

```
id dhanraj
```

Output

```
uid=1001(dhanraj)
gid=1001(dhanraj)
groups=1001(dhanraj),27(sudo)
```

---

# GID (Group ID)

Each group has its own ID.

Example

```
developers

GID = 1005
```

Check

```
id username
```

or

```
groups username
```

---

# Important User Files

Linux stores user information inside four files.

```
/etc/passwd

/etc/shadow

/etc/group

/etc/gshadow
```

Let's understand each.

---

# /etc/passwd

Stores user account information.

It does NOT store passwords anymore.

View

```
cat /etc/passwd
```

Example

```
rahul:x:1001:1001:Rahul Kumar:/home/rahul:/bin/bash
```

Fields

```
username

password placeholder

UID

GID

Comment

Home Directory

Login Shell
```

Diagram

```
rahul:x:1001:1001:Rahul:/home/rahul:/bin/bash

│      │   │    │     │       │          │
│      │   │    │     │       │          │
│      │   │    │     │       │          Login Shell
│      │   │    │     │       Home Directory
│      │   │    │     Comment
│      │   │    GID
│      │   UID
│      Password Placeholder
Username
```

---

# /etc/shadow

Contains encrypted passwords.

View

```
sudo cat /etc/shadow
```

Example

```
rahul:$6$8jfjd.......
```

Only root can read this file.

Check permission

```
ls -l /etc/shadow
```

Example

```
-r-------- root root
```

---

# /etc/group

Contains group information.

View

```
cat /etc/group
```

Example

```
developers:x:1005:rahul,amit
```

Fields

```
Group Name

Password Placeholder

GID

Members
```

---

# /etc/gshadow

Stores secure group passwords.

Normally managed automatically.

---

# Creating Users

## useradd

Basic command

```
sudo useradd john
```

This creates

- User
- UID

But no home directory on some distributions.

---

## Create Home Directory

```
sudo useradd -m john
```

Now

```
/home/john
```

is created.

---

## Specify Shell

```
sudo useradd -s /bin/bash john
```

---

## Specify UID

```
sudo useradd -u 2000 john
```

---

## Specify Home Directory

```
sudo useradd -d /project/john john
```

---

## Create User with Everything

```
sudo useradd

-m

-s /bin/bash

-c "John DevOps"

-U

john
```

---

# adduser

Ubuntu preferred command.

```
sudo adduser john
```

Interactive

```
Password

Full Name

Phone

Room Number

etc.
```

---

# Setting Password

```
sudo passwd john
```

Example

```
New password:

Retype password:
```

---

# Password Expiration

View password details

```
chage -l john
```

Output

```
Password expires

Maximum days

Minimum days
```

---

## Set Maximum Password Age

```
sudo chage -M 90 john
```

Password expires after

```
90 Days
```

---

## Force Password Change

```
sudo passwd -e john
```

Next login

```
User must change password.
```

---

# Lock User

```
sudo passwd -l john
```

Output

```
Password Locked
```

User cannot login.

---

# Unlock User

```
sudo passwd -u john
```

---

# Modify User

## Rename User

```
sudo usermod -l jack john
```

---

## Change Home Directory

```
sudo usermod

-d /home/jack

-m

jack
```

---

## Change Shell

```
sudo usermod

-s /bin/zsh

jack
```

---

## Change UID

```
sudo usermod

-u 2001

jack
```

---

# Delete User

Delete only account

```
sudo userdel john
```

Home directory remains.

---

Delete account and home directory

```
sudo userdel -r john
```

---

# Groups

Groups simplify permission management.

Instead of assigning permissions individually,

assign permissions to groups.

Example

```
Developers

QA

DevOps

Finance

HR
```

---

# Create Group

```
sudo groupadd developers
```

---

# Add User to Group

```
sudo usermod

-aG developers john
```

Explanation

```
-a

Append

G

Secondary Group
```

Never forget **-a**

Without it,

existing groups are removed.

---

# View Groups

```
groups john
```

or

```
id john
```

---

# Change Primary Group

```
sudo usermod

-g developers

john
```

---

# Sudo Access

Some users require administrator privileges.

Instead of logging in as root,

Linux recommends using sudo.

Advantages

- Safer
- Logged
- Temporary privilege
- Better auditing

---

# Debian

```
sudo usermod

-aG sudo

john
```

---

# RHEL

```
sudo usermod

-aG wheel

john
```

---

# Verify

```
groups john
```

Output

```
john sudo developers
```

---

# sudoers File

Edit safely

```
sudo visudo
```

Grant all commands

```
john ALL=(ALL) ALL
```

Passwordless

```
john ALL=(ALL) NOPASSWD:ALL
```

Only Docker

```
john ALL=(ALL)

/usr/bin/docker
```

---

# Difference Between su and sudo

| su | sudo |
|------|------|
| Switch user | Execute one command |
| Requires root password | Requires user password |
| Long session | Temporary privilege |
| Less secure | More secure |

Examples

```
su -
```

```
sudo apt update
```

---

# Useful Commands

```
whoami

id

groups

finger username

last

lastlog

w

who

users

getent passwd

getent group
```

---

# Best Practices

✔ Never login directly as root

✔ Use sudo

✔ Use strong passwords

✔ Remove unused accounts

✔ Disable inactive users

✔ Rotate passwords

✔ Follow least privilege

✔ Use groups instead of individual permissions

✔ Enable account expiration

✔ Review sudo access regularly

---

# Hands-on Lab

Create users

```
sudo useradd -m dev1
sudo useradd -m dev2
```

Create group

```
sudo groupadd developers
```

Add users

```
sudo usermod -aG developers dev1
sudo usermod -aG developers dev2
```

Verify

```
id dev1
groups dev1
```

Set password

```
sudo passwd dev1
```

Lock account

```
sudo passwd -l dev1
```

Unlock account

```
sudo passwd -u dev1
```

Delete account

```
sudo userdel -r dev2
```

---

These concepts are essential for Linux Administration, DevOps, Kubernetes, Cloud Engineering, and System Administration.
