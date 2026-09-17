# aaPanel Linux Installation Script

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-orange.svg?style=for-the-badge&logo=linux" alt="Linux" />
  <img src="https://img.shields.io/badge/Shell-Bash-blue.svg?style=for-the-badge&logo=gnu-bash" alt="Bash" />
  <img src="https://img.shields.io/badge/Architecture-x86__64-brightgreen.svg?style=for-the-badge" alt="64-bit" />
  <img src="https://img.shields.io/badge/Status-Active-success.svg?style=for-the-badge" alt="Active" />
</p>

An automated, 1-click Linux installation script for **aaPanel** — the modern, lightweight, web-based server control panel (LNMP / LAMP).

---

## 📑 Mục lục / Table of Contents
- [Yêu cầu hệ thống / System Requirements](#-yêu-cầu-hệ-thống--system-requirements)
- [Cài đặt nhanh / Quick Installation](#-cài-đặt-nhanh--quick-installation)
- [Cấu hình tường lửa / Firewall Configuration](#-cấu-hình-tường-lửa--firewall-configuration)
- [Lệnh quản trị tiện ích / Useful CLI Commands](#-lệnh-quản-trị-tiện-ích--useful-cli-commands)
- [Tính năng nổi bật / Key Features](#-tính-năng-nổi-bật--key-features)
- [Lưu ý / Disclaimer](#-lưu-ý--disclaimer)

---

## 💻 Yêu cầu hệ thống / System Requirements

| Thành phần / Component | Yêu cầu tối thiểu / Minimum | Khuyến nghị / Recommended |
| :--- | :--- | :--- |
| **Hệ điều hành / OS** | Ubuntu 18.04+, Debian 10+, CentOS 7+, AlmaLinux 8+, RockyLinux 8+ | Ubuntu 22.04 LTS / Debian 11+ |
| **Kiến trúc / Arch** | 64-bit (x86_64 / amd64) | 64-bit (x86_64) |
| **Bộ nhớ / RAM** | 512MB (Pure panel) | 1GB+ (Khuyên dùng cho Nginx + PHP + MySQL) |
| **Dung lượng / Storage** | 100MB trống | 10GB+ cho dữ liệu website & cơ sở dữ liệu |
| **Môi trường / Env** | Máy chủ/VPS mới (Clean/Fresh Server) | Chưa cài sẵn Apache/Nginx/PHP/MySQL |

> [!IMPORTANT]
> Nên cài đặt trên một máy chủ (VPS/Server) mới, chưa cài đặt các dịch vụ web trước đó để tránh xung đột cổng và cấu hình.

---

## 🚀 Cài đặt nhanh / Quick Installation

Đăng nhập vào VPS/Server của bạn bằng quyền `root` qua SSH và chạy một trong hai lệnh sau:

### Cách 1: Sử dụng `curl` (Khuyên dùng)
```bash
curl -sSO https://raw.githubusercontent.com/kingbone2006/aapanelcrack/main/install.sh && bash install.sh
```

### Cách 2: Sử dụng `wget`
```bash
wget -O install.sh https://raw.githubusercontent.com/kingbone2006/aapanelcrack/main/install.sh && bash install.sh
```

---

## 🔑 Đăng nhập bảng điều khiển / Accessing the Panel

Sau khi quá trình cài đặt hoàn tất (thường từ 2 - 5 phút tùy tốc độ mạng và cấu hình VPS), màn hình console sẽ hiển thị thông tin đăng nhập:

```text
==================================================================
Congratulations! Installed successfully!
==================================================================
Internet Address: http://YOUR_SERVER_IP:7800/xxxxxx
Internal Address: http://10.x.x.x:7800/xxxxxx
username: xxxxxxxx
password: xxxxxxxx
==================================================================
```

Hãy sao chép và lưu trữ thông tin này để truy cập vào trình duyệt web.

---

## 🛡️ Cấu hình tường lửa / Firewall Configuration

Để truy cập được vào giao diện aaPanel, bạn cần mở cổng **`7800`** (hoặc cổng do kịch bản tạo ra) cùng các cổng dịch vụ web:

### 1. Trên Cloud Provider (AWS, Google Cloud, Oracle Cloud, Azure, DigitalOcean...)
Vào mục **Security Groups / Firewall Rules** và mở các cổng Inbound (TCP):
- `7800` (Cổng quản trị aaPanel)
- `80`, `443` (HTTP, HTTPS cho website)
- `21`, `20`, `39000-40000` (FTP)
- `3306` (MySQL - nếu cần kết nối từ xa)

### 2. Trên hệ điều hành VPS

**Ubuntu / Debian (UFW):**
```bash
ufw allow 7800/tcp
ufw allow 80/tcp
ufw allow 443/tcp
ufw reload
```

**CentOS / AlmaLinux / RockyLinux (Firewalld):**
```bash
firewall-cmd --permanent --zone=public --add-port=7800/tcp
firewall-cmd --permanent --zone=public --add-port=80/tcp
firewall-cmd --permanent --zone=public --add-port=443/tcp
firewall-cmd --reload
```

---

## ⚡ Lệnh quản trị tiện ích / Useful CLI Commands

Khi đăng nhập SSH, bạn có thể sử dụng công cụ dòng lệnh `bt` để quản lý panel bất kỳ lúc nào:

| Lệnh / Command | Chức năng / Function |
| :--- | :--- |
| `bt` | Mở menu quản trị toàn diện aaPanel |
| `bt 1` | Khởi động lại dịch vụ panel (Restart panel) |
| `bt 2` | Dừng dịch vụ panel (Stop panel) |
| `bt 3` | Bắt đầu dịch vụ panel (Start panel) |
| `bt 5` | Đổi mật khẩu tài khoản quản trị (Change password) |
| `bt 6` | Đổi tên đăng nhập quản trị (Change username) |
| `bt 8` | Đổi cổng truy cập panel (Change port) |
| `bt 14` | Xem lại thông tin đăng nhập mặc định (Show default login info) |
| `bt 16` | Sửa chữa / cập nhật lại panel (Fix panel) |

---

## 🌟 Tính năng nổi bật / Key Features

- **Giao diện Web trực quan**: Quản lý toàn bộ máy chủ Linux dễ dàng qua trình duyệt web mà không cần thuộc nhiều câu lệnh Linux.
- **Cài đặt LNMP / LAMP 1-Click**: Tự động cài đặt và tối ưu hóa Nginx, Apache, MySQL, PHP (đa phiên bản từ 5.6 đến 8.x).
- **Quản lý Website & Tên miền**: Thêm website, cấu hình Reverse Proxy, chuyển hướng HTTP sang HTTPS trong vài giây.
- **SSL Let's Encrypt miễn phí**: Tự động cấp phát và tự động gia hạn chứng chỉ SSL Let's Encrypt cho mọi tên miền.
- **Quản lý Database & FTP**: Tạo cơ sở dữ liệu, quản lý phpMyAdmin, tạo tài khoản FTP nhanh chóng.
- **Trình duyệt file trực tuyến**: File Manager tích hợp sẵn công cụ giải nén zip/tar và trình soạn thảo code trực quan.
- **Bảo mật & Giám sát**: Tích hợp tường lửa, chống DDOS cơ bản, quét virus và theo dõi biểu đồ tải CPU, RAM, Network thời gian thực.

---

## 📄 Lưu ý / Disclaimer

- Repository này phục vụ mục đích nghiên cứu, học tập và triển khai thử nghiệm quản trị máy chủ Linux.
- Vui lòng tuân thủ các quy định và điều khoản sử dụng của nhà phát triển chính thức.
