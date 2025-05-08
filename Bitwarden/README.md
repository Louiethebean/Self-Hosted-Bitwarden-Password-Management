# 🛡️ Bitwarden Self-Hosted Installation Guide

This repository provides step-by-step instructions to self-host the Bitwarden password management service on both **Linux** and **Windows** platforms using Docker.

---

## 📘 Linux Installation Guide

Official Docs: https://bitwarden.com/help/install-on-premise-linux/

### 🧰 Prerequisites

- OS: Ubuntu 20.04+ / Debian / CentOS / RHEL
- Access: Root or sudo
- Installed:
  - Docker
  - Docker Compose
  - curl, openssl
- Bitwarden installation ID and key (get at https://bitwarden.com/host)

### 🧱 Steps

1. **Create Bitwarden Directory**
    ```bash
    mkdir -p /opt/bitwarden
    cd /opt/bitwarden
    ```

2. **Download Bitwarden Installation Script**
    ```bash
    curl -Lso bitwarden.sh https://vault.bitwarden.com/download/?app=self-host&platform=linux
    chmod +x bitwarden.sh
    ```

3. **Run the Installer**
    ```bash
    ./bitwarden.sh install
    ```
    - Enter your domain name
    - Configure SSL (Let's Encrypt or manual)
    - Provide your Bitwarden installation ID and key

4. **Start Bitwarden**
    ```bash
    ./bitwarden.sh start
    ```

---

## 🖥️ Windows Installation Guide

Official Docs: https://bitwarden.com/help/install-on-premise-windows/

### 🧰 Prerequisites

- OS: Windows 10/11 or Windows Server 2019+
- Installed:
  - Docker Desktop
  - Git for Windows (optional)
- Bitwarden installation ID and key

### 🧱 Steps

1. **Create Installation Directory**
    ```powershell
    mkdir C:\Bitwarden
    cd C:\Bitwarden
    ```

2. **Download Installation Script**
    - Visit: [https://bitwarden.com/host](https://bitwarden.com/host)
    - Download the Windows PowerShell installation script
    - Save as `bitwarden.ps1` in your directory

3. **Run PowerShell as Administrator**, then execute:
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force
    .\bitwarden.ps1 -install
    ```

4. **Follow Prompts**
    - Provide domain and SSL preferences
    - Enter installation ID and key

5. **Start Bitwarden**
    ```powershell
    .\bitwarden.ps1 -start
    ```

---

## 🧾 Notes

- Use `bitwarden.sh` or `bitwarden.ps1` to manage the server.
- Update regularly using `update` flags or re-running the script.
- Backup and restore procedures are similar across platforms (ensure Docker volumes are included).

---

## 📚 References

- [Bitwarden On-Premise Guide (Linux)](https://bitwarden.com/help/install-on-premise-linux/)
- [Bitwarden On-Premise Guide (Windows)](https://bitwarden.com/help/install-on-premise-windows/)
- [Docker Docs](https://docs.docker.com/)