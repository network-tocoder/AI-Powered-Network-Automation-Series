# 🚀 Network Automation Series

![Network Coder Banner](assets/banner.jpg)

**Network | AI | Tool Integration | Virtual LAB | Automation**

[![YouTube](https://img.shields.io/badge/YouTube-NetworkCoder-red?style=for-the-badge&logo=youtube)](https://youtube.com/@NetworkCoder)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=for-the-badge&logo=github)](https://github.com/network-tocoder)

---

## 📺 Video Index

| # | Video | Topic | Resources |
|---|-------|-------|-----------|
| 1 | [EVE-NG Installation](#video-1-eve-ng-installation--first-virtual-lab) | EVE-NG, Virtual Lab Setup | [📁 Folder](./video-01/) |
| 2 | Coming Soon | TBD | [📁 Folder](./video-02/) |
| 3 | Coming Soon | TBD | [📁 Folder](./video-03/) |
| 4 | Coming Soon | TBD | [📁 Folder](./video-04/) |
| 5 | Coming Soon | TBD | [📁 Folder](./video-05/) |
| 6 | [NetBox Docker Setup](#video-6-netbox-docker-installation) | NetBox, Docker, EVE-NG | [📁 Folder](./video-06/) |
| 7 | [Ansible FortiGate Automation](#video-7-ansible-fortigate-automation) | Ansible, FortiGate, Vault | [📁 Folder](./video-07/) |

---

## 🛠️ Tech Stack

![EVE-NG](https://img.shields.io/badge/EVE--NG-00A98F?style=for-the-badge&logo=vmware&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NetBox](https://img.shields.io/badge/NetBox-0078D4?style=for-the-badge&logo=buffer&logoColor=white)
![FortiGate](https://img.shields.io/badge/FortiGate-EE3124?style=for-the-badge&logo=fortinet&logoColor=white)
![Cisco](https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)

---

## Video 1: EVE-NG Installation & First Virtual Lab

### 📋 Overview

Complete guide to installing EVE-NG (Emulated Virtual Environment - Next Generation) and creating your first virtual network lab.

### 🎯 What You'll Learn

- Download and install EVE-NG
- Configure EVE-NG virtual machine
- Access EVE-NG web interface
- Create your first lab topology
- Add and connect network devices

### 💻 System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| CPU | 4 Cores (VT-x/AMD-V enabled) | 8+ Cores |
| RAM | 8 GB | 16+ GB |
| Storage | 50 GB | 100+ GB SSD |
| Hypervisor | VMware/VirtualBox/Bare Metal | VMware Workstation Pro |

### 💻 Commands

<details>
<summary>1. Download EVE-NG</summary>

```bash
# Download EVE-NG Community ISO/OVA from:
# https://www.eve-ng.net/index.php/download/
```

</details>

<details>
<summary>2. Initial Setup After Boot</summary>

```bash
# Default credentials
Username: root
Password: eve

# The setup wizard will guide you through:
# - Hostname configuration
# - Domain name
# - Network configuration (DHCP or Static IP)
# - Root password change
```

</details>

<details>
<summary>3. Update EVE-NG</summary>

```bash
# Update system packages
apt update && apt upgrade -y

# Fix any broken packages
apt --fix-broken install
```

</details>

<details>
<summary>4. Access Web Interface</summary>

```bash
# Find your EVE-NG IP address
ip addr show

# Or
hostname -I

# Access in browser: http://YOUR-EVE-NG-IP
# Default web credentials:
# Username: admin
# Password: eve
```

</details>

<details>
<summary>5. Upload Device Images</summary>

```bash
# Connect via SFTP/SCP
# Upload images to appropriate folders:

# Cisco IOS/IOL
/opt/unetlab/addons/iol/bin/

# Cisco VIRL/QEMU images
/opt/unetlab/addons/qemu/

# Fix permissions after upload
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions
```

</details>

<details>
<summary>6. Useful EVE-NG Commands</summary>

```bash
# Check EVE-NG service status
systemctl status eve-ng

# Restart EVE-NG services
systemctl restart eve-ng

# Fix permissions (run after adding images)
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions

# Stop all running nodes
/opt/unetlab/wrappers/unl_wrapper -a stopall
```

</details>

### 🔗 Resources

- [EVE-NG Official Website](https://www.eve-ng.net/)
- [EVE-NG Documentation](https://www.eve-ng.net/index.php/documentation/)

---

## Video 6: NetBox Docker Installation

### 📋 Overview

Step-by-step guide to install NetBox using Docker Compose on Ubuntu/EVE-NG.

### 💻 Commands

<details>
<summary>1. Update System & Install Docker</summary>

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

# Check versions
docker --version
docker-compose --version
```

</details>

<details>
<summary>2. Configure Docker Permissions</summary>

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Confirm group entry
getent group docker
```

</details>

<details>
<summary>3. Download & Configure NetBox</summary>

```bash
# Clone NetBox Docker repository
git clone -b release https://github.com/netbox-community/netbox-docker.git

# Enter directory
cd netbox-docker

# Create override file for port mapping
cp docker-compose.override.yml.example docker-compose.override.yml
```

</details>

<details>
<summary>4. Start NetBox</summary>

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
<summary>5. Troubleshooting</summary>

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
<summary>6. Create Superuser</summary>

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

Learn how to automate FortiGate firewalls using Ansible with secure credential storage.

### 📁 Project Structure

```
ansible-project/
├── ansible.cfg
├── inventory/
│   └── hosts
├── host_vars/
│   └── Forti-FW-1.yml (encrypted)
└── playbooks/
    ├── fortigate_system_info.yml
    └── fortigate_create_policy.yml
```

### 💻 Commands

<details>
<summary>1. Install FortiGate Collection</summary>

```bash
# Check Ansible version
ansible --version

# Install FortiGate collection
ansible-galaxy collection install fortinet.fortios

# Verify installation
ansible-galaxy collection list | grep fortinet
```

</details>

<details>
<summary>2. Ansible Vault Commands</summary>

```bash
# Create encrypted vault file
ansible-vault create host_vars/Forti-FW-1.yml

# View decrypted content
ansible-vault view host_vars/Forti-FW-1.yml

# Edit encrypted file
ansible-vault edit host_vars/Forti-FW-1.yml

# Change vault password
ansible-vault rekey host_vars/Forti-FW-1.yml
```

</details>

<details>
<summary>3. Inventory Verification</summary>

```bash
# List all inventory with vault decryption
ansible-inventory --list -i inventory/hosts --ask-vault-pass

# Check specific host variables
ansible-inventory --host Forti-FW-1 --ask-vault-pass
```

</details>

<details>
<summary>4. Run Playbooks</summary>

```bash
# Run system info playbook
ansible-playbook playbooks/fortigate_system_info.yml --ask-vault-pass

# Run with verbose output
ansible-playbook playbooks/fortigate_system_info.yml --ask-vault-pass -vvv

# Dry run (check mode)
ansible-playbook playbooks/fortigate_create_policy.yml --ask-vault-pass --check
```

</details>

<details>
<summary>5. Inventory File Example</summary>

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
| Fortinet Docs | [docs.fortinet.com](https://docs.fortinet.com/) |

---

## 🤝 Connect With Me

[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com/@NetworkCoder)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/YourProfile)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ **If you find this helpful, please star the repo!** ⭐
