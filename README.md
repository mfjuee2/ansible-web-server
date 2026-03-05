# Web Server Provisioning with Ansible

This repository contains an Ansible playbook to automate the provisioning and hardening of a production-ready web server. It sets up a secure LEMP-like stack optimized for modern web applications.

## 🚀 Architecture & Stack
* **OS:** Ubuntu 22.04 / 24.04 LTS
* **Web Server:** Nginx (with security headers & optimized for PHP-FPM)
* **Caching:** Redis (configured with `allkeys-lru` policy)
* **Monitoring:** Zabbix Agent
* **Containerization:** Docker & Docker Compose ready
* **Security (Hardening):** Custom SSH port, disabled root login, UFW firewall, strict Sysctl network tuning (anti-DDoS/Spoofing), and user shell limits.

## 📂 Project Structure
* `roles/hardening/` - OS security, firewall, sysctl tuning, and user management.
* `roles/webstack/` - Installation and configuration of Nginx, PHP, Redis, and Zabbix.
* `group_vars/all.yml` - Global variables (Domain name, SSH ports, users).

## 🛠️ Usage

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/ansible-web-server.git](https://github.com/yourusername/ansible-web-server.git)
   cd ansible-web-server
   ssh-copy-id -i ~/.ssh/ed25519_ubuntu.pub user@192.168.218.129
   ansible-playbook -i inventory.yml site.yml -K -e "ansible_port=22"
   ```