# ⚡ aaPanel Linux - 1-Click Automated Installation Script

<p align="center">
  <a href="README.md"><strong>🇺🇸 English (Current)</strong></a> &nbsp;|&nbsp; 
  <a href="README_VI.md"><strong>🇻🇳 Xem bản Tiếng Việt</strong></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/OS-CentOS_|_Ubuntu_|_Debian_|_AlmaLinux_|_Rocky-E95420?logo=linux&logoColor=white" alt="Linux OS" />
  <img src="https://img.shields.io/badge/Panel-aaPanel_Linux-blue" alt="aaPanel" />
  <img src="https://img.shields.io/badge/Type-Shell_Script-brightgreen?logo=gnubash&logoColor=white" alt="Shell Script" />
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT" />
</p>

<p align="center">
  <b>High-speed 1-click installation script for aaPanel (Web Hosting Control Panel) on popular Linux distributions (Ubuntu, Debian, CentOS, AlmaLinux, Rocky Linux).</b>
</p>

---

## 📖 Overview

**aaPanel** is an intuitive, lightweight, modular open-source hosting control panel that helps webmasters manage websites, databases, FTP accounts, SSL certificates, Python / Node.js runtimes, and Docker containers with a few clicks.

This repository provides an automated installation script (`install.sh`) that streamlines the installation process, automatically downloads required system dependencies, configures system firewalls, and provisions initial admin credentials.

---

## 🚀 1-Click Installation (Quick Start)

Connect to your VPS/Server via SSH using `root` privileges and run:

### Using `wget`:
```bash
wget -O install.sh https://raw.githubusercontent.com/kingbone2006/aapanelcrack/main/install.sh && bash install.sh
```

### Or using `curl`:
```bash
curl -sSO https://raw.githubusercontent.com/kingbone2006/aapanelcrack/main/install.sh && bash install.sh
```

> [!NOTE]
> The installation typically takes **2 to 5 minutes** depending on your network bandwidth and server CPU performance. Once completed, your access URL, default port, username, and password will be displayed directly in the terminal output.

---

## 💻 Supported Operating Systems

| Distribution | Minimum Version | Recommended Version |
| :--- | :--- | :--- |
| **Ubuntu** | 16.04+ | 20.04 LTS / 22.04 LTS |
| **Debian** | 9.0+ | 10 / 11 / 12 |
| **CentOS** | 7.1+ | 7.x / 8.x |
| **AlmaLinux** | 8.x+ | 8.x / 9.x |
| **Rocky Linux** | 8.x+ | 8.x / 9.x |

### Minimum Hardware Requirements:
- **RAM**: Minimum 512MB (1GB+ recommended; 2GB+ if running MySQL/MariaDB and LAMP/LNMP stack).
- **Disk Space**: At least 1GB of free space.
- **Clean OS**: It is strongly recommended to install on a fresh Linux operating system (without pre-installed Apache, Nginx, or MySQL).

---

## 🛡️ Firewall & Port Forwarding

Make sure to open the following ports in your Cloud Provider's Security Groups (AWS, Cloudflare, DigitalOcean, Linode, Vultr, Google Cloud...) or system firewall (`ufw` / `firewalld`):

| Port | Protocol | Purpose |
| :--- | :--- | :--- |
| **7800** (or **8888**) | TCP | aaPanel Web GUI Access Port |
| **80** | TCP | Standard HTTP Web Traffic |
| **443** | TCP | Encrypted HTTPS / SSL Web Traffic |
| **20, 21** | TCP | FTP Data Transfer & Control |
| **3306** | TCP | Remote MySQL / MariaDB (optional) |
| **888** | TCP | phpMyAdmin Access Port (optional) |

---

## 🛠️ CLI Management Tool (`bt` Command)

After installation, aaPanel provides a powerful command-line interface tool named `bt`. Run `bt` in your SSH terminal at any time to open the management menu:

```bash
bt
```

### Common Shortcut Commands:
- `bt 1` : Restart panel services
- `bt 2` : Stop panel services
- `bt 3` : Start panel services
- `bt 5` : Change / reset panel administrator password
- `bt 6` : Change / reset panel administrator username
- `bt 8` : Change panel web port
- `bt 14` : Display default login credentials & security entrance URL
- `bt 16` : Clear panel domain / security entry bindings in emergency situations

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
