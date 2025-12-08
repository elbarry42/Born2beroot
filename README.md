# Born2beRoot – Building a Secure Linux Server from Scratch 🐧🔐

<div align="center">

<a>![42 Badge](https://github.com/elbarry42/elbarry42/blob/main/42_badges/born2beroote.png)</a>

</div>

Welcome to **Born2beRoot**! 🎉 This system administration project focuses on creating, configuring, and securing a fully functional Linux server inside a virtual machine. It offers an essential introduction to virtualization, server management, security hardening, scripting, and core DevOps concepts.

---

## 📝 Project Overview

Born2beRoot consists of installing a minimal Debian or Rocky Linux system, securing it, and configuring essential services without relying on any graphical interface.

The project includes:

* Setting up encrypted partitions with **LVM**
* Configuring users, password policies, and sudo restrictions
* Securing SSH access on a custom port
* Enforcing a firewall
* Writing a system monitoring script that broadcasts real-time data

The goal is to understand how a server is built, secured, administered, and monitored—just like a real production environment.

---

## 🔧 Core Configuration Requirements

### 🔹 Operating System

You must choose between:

* **Debian (recommended for beginners)**
* **Rocky Linux (uses SELinux by default)**

No graphical environment is allowed—this project is fully command-line based.

---

### 🔹 Partitioning (LVM + Encryption)

Create at least **two encrypted partitions** using LVM:

* Physical Volumes (PV)
* Volume Group (VG)
* Logical Volumes (LV)

This teaches how storage is structured and protected on Linux servers.

---

### 🔹 User & Host Configuration

* Hostname must follow the format: `<login>42`
* Create a user matching your 42 login
* Add the user to:

  * `sudo`
  * `user42`

---

### 🔹 Password Policy

A strict password policy must be enforced:

* Valid for 30 days
* 2 days minimum before modification
* Warning 7 days before expiration
* At least 10 characters, including uppercase, lowercase, and digits
* No more than 3 identical consecutive characters
* Must not contain the username

---

### 🔹 Sudo Configuration

Sudo must be hardened with:

* Maximum 3 password attempts
* Custom error message
* All sudo commands logged to `/var/log/sudo/`
* TTY mode enabled
* Restricted PATH

---

### 🔹 SSH & Firewall

* SSH must run **only on port 4242**
* Root login via SSH is forbidden
* Use a firewall:

  * **UFW** on Debian
  * **firewalld** on Rocky Linux
* Only port 4242 should remain open

---

### 🔹 Monitoring Script

A Bash script `monitoring.sh` must:

* Display system information (CPU load, RAM, disk, users, IP, MAC, LVM, etc.)
* Run automatically every **10 minutes** via cron
* Broadcast output using `wall`

---

## 📂 Project Structure

```
Born2beroot/
│── signature.txt      # SHA1 signature of the VM disk
└── monitoring.sh      # Monitoring script
```

---

## 🛠️ Usage

### Retrieving the VM Signature

Generate the SHA1 hash of your `.vdi` or `.qcow2` file using:

* Linux: `sha1sum disk.vdi`
* Windows: `certUtil -hashfile disk.vdi sha1`
* macOS: `shasum disk.vdi`

Place the resulting hash inside **signature.txt**.

---

### Activating the Monitoring Script

Add the cron job:

```
sudo crontab -e
*/10 * * * * /path/to/monitoring.sh
```

---

## 🧠 Learning Outcomes

Through this project, you learn how to:

✅ Install and manage a Linux server
✅ Configure encrypted storage with LVM
✅ Apply strict security and password policies
✅ Harden sudo and SSH access
✅ Use firewalls (UFW / firewalld)
✅ Write automated Bash scripts
✅ Understand SELinux/AppArmor basics
✅ Work like a real system administrator

---

## ⚙️ Technology Comparisons

### Debian vs Rocky Linux

| Feature         | Debian   | Rocky Linux              |
| --------------- | -------- | ------------------------ |
| Difficulty      | Easier   | More advanced            |
| Security        | AppArmor | SELinux                  |
| Package Manager | apt      | dnf                      |
| Recommended     | ✔️       | ⚠️ For experienced users |

### UFW vs firewalld

| UFW                 | firewalld            |
| ------------------- | -------------------- |
| Simple and static   | Dynamic and flexible |
| Ideal for beginners | More advanced        |

### VirtualBox vs UTM

| VirtualBox     | UTM                       |
| -------------- | ------------------------- |
| Faster         | Slower (QEMU)             |
| Multi-platform | macOS-focused             |
| Easier setup   | More configuration needed |

---

## 📚 Resources

* Debian Handbook
* Rocky Linux Documentation
* AppArmor & SELinux Guides
* VirtualBox Manual
* UFW & firewalld documentation
* LVM official guides
* Bash manual pages

---

## 🤖 AI Usage

AI was used **only** to help structure and write this README in a clear, readable format.
All system configuration and scripting were done manually.

---

## ✔️ Evaluation Checklist

* [ ] Correct hostname
* [ ] User + groups configured
* [ ] Password policy active
* [ ] Sudo restrictions implemented
* [ ] SSH on port 4242 only
* [ ] Firewall active
* [ ] LVM encrypted partitions created
* [ ] monitoring.sh functional + cron enabled
* [ ] signature.txt matches VM disk

---

## 🏁 Conclusion

Born2beRoot provides essential exposure to Linux system administration, preparing you for DevOps, cybersecurity, and advanced 42 projects such as Inception and NetPractice.

✨ Thanks for exploring the Born2beRoot project! 🚀
