*This project was completed as part of the 42 curriculum by elbarry.*

# Born2beRoot – Building a Secure Linux Server from Scratch 🐧🔐

<div align="center">

![42 Badge](https://github.com/elbarry42/elbarry42/blob/main/42_badges/born2beroote.png)

</div>

Welcome to **Born2beRoot**! 🎉  
This system administration project introduces the fundamentals of **virtualization**, **Linux server setup**, and **security hardening** by building a fully functional and secure server from scratch.

---

## 📝 Description

**Born2beRoot** aims to teach the basics of system administration by guiding students through the installation, configuration, and securing of a Linux operating system inside a virtual machine.

The project focuses on:

* Understanding how a Linux server works internally
* Applying strict security rules
* Managing users, permissions, and services
* Automating system monitoring with Bash

The entire setup is done **without any graphical interface**, simulating a real-world production server environment.

---

## ⚙️ Instructions

### 🔹 Virtualization Environment

* Virtual machine created using **VirtualBox** (or **UTM** if VirtualBox is unavailable)
* The use of **snapshots is strictly forbidden**
* Only the file `signature.txt` must be submitted in the Git repository

---

### 🔹 Operating System Choice

This project is implemented using **Debian (latest stable version)**.

**Why Debian?**

* Beginner-friendly and well-documented
* Stable release cycle
* Widely used on production servers

Restrictions:

* No graphical interface allowed (X.org, Wayland, etc.)
* AppArmor is available on Debian and may be enabled by default

---

### 🔹 Disk Partitioning (LVM + Encryption)

* At least **two encrypted partitions** must be created
* Partitioning must use **LVM**:

  * Physical Volumes (PV)
  * Volume Groups (VG)
  * Logical Volumes (LV)

This ensures data security and flexible disk management.

---

### 🔹 Hostname & User Configuration

* Hostname format: `<login>42`
* A user with your 42 login must be created
* The user must belong to the following groups:

  * `sudo`
  * `user42`

---

### 🔹 Password Policy

A strong password policy must be enforced:

* Password expires every **30 days**
* Minimum **2 days** before modification
* Warning **7 days** before expiration
* Minimum **10 characters**
* Must contain:

  * Uppercase letter
  * Lowercase letter
  * Number
* No more than **3 identical consecutive characters**
* Must not contain the username

The policy applies to all users, including root.

---

### 🔹 Sudo Configuration

Sudo must be configured with strict rules:

* Maximum **3 authentication attempts**
* Custom error message on wrong password
* All sudo actions logged in `/var/log/sudo/`
* **TTY mode enabled**
* Restricted PATH:

```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```

---

### 🔹 SSH & Firewall

* SSH must run **only on port 4242**
* SSH login as root is **forbidden**
* Firewall must be active at startup:

  * **UFW** for Debian
  * **firewalld** for Rocky Linux
* Only port **4242** is open (mandatory part)

---

### 🔹 Monitoring Script

A Bash script named `monitoring.sh` must:

* Display system information on all terminals using `wall`
* Run **every 10 minutes** using `cron`
* Show the following information:

  * OS architecture and kernel version
  * Number of physical CPUs
  * Number of virtual CPUs
  * RAM usage and percentage
  * Disk usage and percentage
  * CPU usage percentage
  * Last reboot date and time
  * LVM status
  * Number of active TCP connections
  * Number of logged-in users
  * IPv4 and MAC address
  * Number of sudo commands executed

---

## 📂 Project Structure

```

Born2beRoot/
│── signature.txt      # SHA1 signature of the VM disk

```

---

## 🧠 Design Choices & Comparisons

### Debian vs Rocky Linux

This project was completed on **Debian**, chosen for its stability and accessibility for newcomers to system administration.

| Feature         | Debian            | Rocky Linux |
| --------------- | ----------------- | ----------- |
| Difficulty      | Beginner-friendly | Advanced    |
| Security        | AppArmor          | SELinux     |
| Package Manager | apt               | dnf         |
| Recommendation  | ✅ Chosen          | ⚠️          |

### AppArmor vs SELinux

* **AppArmor**: Easier to configure, profile-based
* **SELinux**: More powerful, stricter, policy-based

### UFW vs firewalld

* **UFW**: Simple and static, ideal for beginners
* **firewalld**: Dynamic and flexible, enterprise-oriented

### VirtualBox vs UTM

* **VirtualBox**: Faster, cross-platform, easier setup
* **UTM**: macOS-focused, uses QEMU, more configuration required

---

## ⭐ Bonus Part

The bonus part was **not implemented**.  
Only the **mandatory part** of the project was completed.

---

## 📚 Resources

* Debian Documentation
* Rocky Linux Documentation
* VirtualBox & UTM Manuals
* LVM Official Documentation
* Bash & Cron Manuals

---

### 🤖 AI Usage

AI tools were used **only for documentation assistance**.  
All system configuration and scripting were done manually and fully understood.

---

## 📦 Submission

* Only `signature.txt` must be submitted
* The virtual machine must **never** be pushed to Git
* The SHA1 signature must exactly match the VM disk
* Snapshots are strictly forbidden

---

✨ Thanks for checking out my **Born2beRoot** project! 🚀
