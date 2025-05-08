# 🛡️ Bitwarden Self-Hosted Installation Guide

This guide provides detailed instructions for installing and deploying Bitwarden on-premises using Docker, applicable to both Linux and Windows systems.

---

## 🧰 Prerequisites

- **System Requirements:**
  - **Processor:** x64, 2GHz dual core
  - **Memory:** 4GB RAM
  - **Storage:** 25GB
- **Software Requirements:**
  - **Linux:**
    - Docker Engine 26+ and Docker Compose
    - `curl`, `unzip`, `openssl`
  - **Windows:**
    - Docker Desktop
    - PowerShell
- **Additional Requirements:**
  - Public domain name (e.g., `vault.example.com`)
  - Bitwarden installation ID and key (obtain from https://bitwarden.com/host/)

---

## 🐧 Linux Installation Steps

1. **Create Bitwarden User and Directory:**
    ```bash
    sudo adduser bitwarden
    sudo passwd bitwarden
    sudo groupadd docker
    sudo usermod -aG docker bitwarden
    sudo mkdir /opt/bitwarden
    sudo chmod -R 700 /opt/bitwarden
    sudo chown -R bitwarden:bitwarden /opt/bitwarden
    ```

2. **Switch to Bitwarden User:**
    ```bash
    su - bitwarden
    cd /opt/bitwarden
    ```

3. **Download and Run Installation Script:**
    ```bash
    curl -Lso bitwarden.sh https://vault.bitwarden.com/download/?app=self-host&platform=linux
    chmod +x bitwarden.sh
    ./bitwarden.sh install
    ```

4. **Start Bitwarden:**
    ```bash
    ./bitwarden.sh start
    ```

---

## 🪟 Windows Installation Steps

1. **Install Docker Desktop:**
    - Download and install Docker Desktop from https://www.docker.com/products/docker-desktop/

2. **Create Installation Directory:**
    ```powershell
    mkdir C:\Bitwarden
    cd C:\Bitwarden
    ```

3. **Download Installation Script:**
    - Obtain the PowerShell installation script from https://bitwarden.com/host/
    - Save it as `bitwarden.ps1` in your installation directory.

4. **Run Installation Script:**
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force
    .\bitwarden.ps1 -install
    ```

5. **Start Bitwarden:**
    ```powershell
    .\bitwarden.ps1 -start
    ```

---

## 🔧 Configuration and Management

- **Environment Variables:**
    - Configure in `./bwdata/env/global.override.env`

- **Commands:**
    ```bash
    ./bitwarden.sh start
    ./bitwarden.sh stop
    ./bitwarden.sh restart
    ./bitwarden.sh update
    ./bitwarden.sh updateself
    ```

---

## 🔒 SSL Certificates

- **Let's Encrypt:** Auto configuration during install
- **Manual:** Place certs in `./bwdata/ssl/<your-domain>/`

---

## 🛡️ Backup and Restore

- **Backup:**
    ```bash
    tar -czvf bitwarden-backup.tar.gz /opt/bitwarden/bwdata
    ```

- **Restore:**
    ```bash
    tar -xzvf bitwarden-backup.tar.gz -C /opt/bitwarden/
    ./bitwarden.sh rebuild
    ./bitwarden.sh start
    ```

---

## 📚 References

- [Linux Install Guide](https://bitwarden.com/help/install-on-premise-linux/)
- [Windows Install Guide](https://bitwarden.com/help/install-on-premise-windows/)
- [Manual Deployment](https://bitwarden.com/help/install-on-premise-manual/)