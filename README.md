# 🚀 Network Automation Series

Welcome to my Network Automation learning journey! This repository contains all the commands, configurations, and resources from my video tutorials.

[![YouTube](https://img.shields.io/badge/YouTube-NetworkCoder-red?style=for-the-badge&logo=youtube)](https://youtube.com/@YourChannel)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=for-the-badge&logo=github)](https://github.com/YourUsername)

---

## 📺 Video Index

| # | Video | Topic | Resources |
|---|-------|-------|-----------|
| 1 | Coming Soon | TBD | [📁 Folder](./video-01/) |
| 2 | Coming Soon | TBD | [📁 Folder](./video-02/) |
| 3 | Coming Soon | TBD | [📁 Folder](./video-03/) |
| 4 | Coming Soon | TBD | [📁 Folder](./video-04/) |
| 5 | Coming Soon | TBD | [📁 Folder](./video-05/) |
| 6 | [NetBox Docker Setup](#video-6-netbox-docker-installation) | NetBox, Docker, EVE-NG | [📁 Folder](./video-06/) |
| 7 | [Ansible FortiGate Automation](#video-7-ansible-fortigate-automation) | Ansible, FortiGate, Vault | [📁 Folder](./video-07/) |

---

## 🛠️ Tech Stack

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![NetBox](https://img.shields.io/badge/NetBox-0078D4?style=flat-square&logo=netbox&logoColor=white)
![FortiGate](https://img.shields.io/badge/FortiGate-EE3124?style=flat-square&logo=fortinet&logoColor=white)

---

## Video 6: NetBox Docker Installation

### 📋 Overview

Step-by-step guide to install NetBox using Docker Compose on Ubuntu/EVE-NG. NetBox is a powerful IPAM (IP Address Management) and DCIM (Data Center Infrastructure Management) tool.

### 🎯 What You'll Learn

- Install Docker and Docker Compose on Ubuntu
- Deploy NetBox using docker-compose
- Configure port mappings and overrides
- Troubleshoot common Docker issues
- Create NetBox superuser

### 💻 Commands

<details>
<summary><b>1. Update System & Install Docker</b></summary>

```bash
# Install OpenSSH Server
sudo apt install openssh-server -y

# Update system
sudo apt update && upgrade -y

# Install Docker + Docker Compose
sudo apt install -y docker.io docker-compose

# Start Docker service
sudo systemctl start docker

# Verify Docker is running
systemctl is-active docker
sudo systemctl status docker

# Check versions
docker --version
docker-compose --version
```

</details>

<details>
<summary><b>2. Configure Docker Permissions</b></summary>

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Confirm group entry
getent group docker
```

</details>

<details>
<summary><b>3. Download & Configure NetBox</b></summary>

```bash
# Clone NetBox Docker repository
git clone -b release https://github.com/netbox-community/netbox-docker.git

# Enter directory
cd netbox-docker

# Create override file for port mapping
cp docker-compose.override.yml.example docker-compose.override.yml
```

**Port Mapping:** `8000:8080` (Host:Container)

</details>

<details>
<summary><b>4. Start NetBox</b></summary>

```bash
# Pull images
docker-compose pull

# Start NetBox stack
docker-compose up -d

# Check status
docker-compose ps

# Verify port listening
ss -tuln | grep :8000

# Test web access
curl -I http://localhost:8000
```

</details>

<details>
<summary><b>5. Troubleshooting</b></summary>

```bash
# Restart NetBox container
sudo docker-compose restart netbox

# Stop everything
docker-compose down

# View logs
docker-compose logs
docker-compose logs netbox
docker-compose logs postgres

# Nuclear reset (removes all data!)
docker-compose down -v
docker-compose pull
docker-compose up -d
```

</details>

<details>
<summary><b>6. Create Superuser</b></summary>

```bash
docker-compose exec netbox /opt/netbox/netbox/manage.py createsuperuser
```

</details>

### 🔗 Resources

- [NetBox Documentation](https://docs.netbox.dev/)
- [NetBox Docker GitHub](https://github.com/netbox-community/netbox-docker)

---

## Video 7: Ansible FortiGate Automation

### 📋 Overview

Learn how to automate FortiGate firewalls using Ansible. This video covers installing the FortiGate collection, using Ansible Vault for secure credential storage, and running playbooks.

### 🎯 What You'll Learn

- Install Fortinet Ansible collection
- Secure credentials with Ansible Vault
- Create and run FortiGate playbooks
- Troubleshoot with verbose output

### 📁 Project Structure

```
ansible-project/
├── ansible.cfg
├── inventory/
│   └── hosts
├── host_vars/
│   └── Forti-FW-1.yml (encrypted)
├── group_vars/
│   └── fortigates.yml (optional)
└── playbooks/
    ├── fortigate_system_info.yml
    └── fortigate_create_policy.yml
```

### 💻 Commands

<details>
<summary><b>1. Install FortiGate Collection</b></summary>

```bash
# Check Ansible version
ansible --version

# Install FortiGate collection
ansible-galaxy collection install fortinet.fortios

# Verify installation
ansible-galaxy collection list | grep fortinet

# List all collections
ansible-galaxy collection list
```

</details>

<details>
<summary><b>2. Ansible Vault Commands</b></summary>

```bash
# Create encrypted vault file
ansible-vault create host_vars/Forti-FW-1.yml

# View encrypted file (shows encrypted text)
cat host_vars/Forti-FW-1.yml

# View decrypted content
ansible-vault view host_vars/Forti-FW-1.yml

# Edit encrypted file
ansible-vault edit host_vars/Forti-FW-1.yml

# Change vault password
ansible-vault rekey host_vars/Forti-FW-1.yml
```

</details>

<details>
<summary><b>3. Inventory Verification</b></summary>

```bash
# List all inventory with vault decryption
ansible-inventory --list -i inventory/hosts --ask-vault-pass

# Check specific host variables
ansible-inventory --host Forti-FW-1 --ask-vault-pass

# View inventory in YAML format
ansible-inventory --list -i inventory/hosts --ask-vault-pass --yaml
```

</details>

<details>
<summary><b>4. Run Playbooks</b></summary>

```bash
# Run system info playbook
ansible-playbook playbooks/fortigate_system_info.yml --ask-vault-pass

# Run with verbose output
ansible-playbook playbooks/fortigate_system_info.yml --ask-vault-pass -v
ansible-playbook playbooks/fortigate_system_info.yml --ask-vault-pass -vvv

# Create firewall policy
ansible-playbook playbooks/fortigate_create_policy.yml --ask-vault-pass

# Dry run (check mode)
ansible-playbook playbooks/fortigate_create_policy.yml --ask-vault-pass --check

# Using vault password file (for automation)
ansible-playbook playbooks/fortigate_system_info.yml --vault-password-file ~/.vault_pass
```

</details>

### 📝 Configuration Files

<details>
<summary><b>Inventory File (inventory/hosts)</b></summary>

```ini
[fortigates]
Forti-FW-1 ansible_host=192.168.1.111

[fortigates:vars]
ansible_network_os=fortinet.fortios.fortios
ansible_connection=httpapi
ansible_httpapi_use_ssl=yes
ansible_httpapi_validate_certs=no
ansible_httpapi_port=443
```

</details>

<details>
<summary><b>Vault File (host_vars/Forti-FW-1.yml)</b></summary>

```yaml
---
fortios_api_token: your-api-token-here
```

> ⚠️ **Note:** Encrypt this file using `ansible-vault create` or `ansible-vault encrypt`

</details>

### 🔗 Resources

- [Fortinet Ansible Collection](https://galaxy.ansible.com/fortinet/fortios)
- [FortiOS Ansible Docs](https://ansible-galaxy-fortios-docs.readthedocs.io/)

---

## 📚 Additional Resources

| Resource | Link |
|----------|------|
| EVE-NG | [eve-ng.net](https://www.eve-ng.net/) |
| NetBox | [netbox.dev](https://netbox.dev/) |
| Ansible Docs | [docs.ansible.com](https://docs.ansible.com/) |
| Docker Docs | [docs.docker.com](https://docs.docker.com/) |

---

## 🤝 Connect With Me

- 📺 [YouTube - NetworkCoder](https://youtube.com/@YourChannel)
- 💼 [LinkedIn](https://linkedin.com/in/YourProfile)
- 🐦 [Twitter](https://twitter.com/YourHandle)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ **If you find this helpful, please star the repo!** ⭐
