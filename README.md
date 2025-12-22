<![CDATA[<!-- Banner -->
<p align="center">
  <img src="./assets/banner.jpg" alt="Network Coder Banner" width="100%">
</p>

<h1 align="center">🚀 Network Automation Series</h1>

<p align="center">
  <strong>Network | AI | Tool Integration | Virtual LAB | Automation</strong>
</p>

<p align="center">
  <a href="https://youtube.com/@NetworkCoder"><img src="https://img.shields.io/badge/YouTube-NetworkCoder-red?style=for-the-badge&logo=youtube" alt="YouTube"></a>
  <a href="https://github.com/NetworkCoder"><img src="https://img.shields.io/badge/GitHub-Follow-black?style=for-the-badge&logo=github" alt="GitHub"></a>
</p>

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

<p align="center">
  <img src="https://img.shields.io/badge/EVE--NG-00A98F?style=for-the-badge&logo=vmware&logoColor=white" alt="EVE-NG">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white" alt="Ansible">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/NetBox-0078D4?style=for-the-badge&logo=buffer&logoColor=white" alt="NetBox">
  <img src="https://img.shields.io/badge/FortiGate-EE3124?style=for-the-badge&logo=fortinet&logoColor=white" alt="FortiGate">
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white" alt="Cisco">
</p>

---

## Video 1: EVE-NG Installation & First Virtual Lab

### 📋 Overview

Complete guide to installing EVE-NG (Emulated Virtual Environment - Next Generation) and creating your first virtual network lab. EVE-NG allows you to emulate real network devices for learning, testing, and development.

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
<summary><b>1. Download EVE-NG</b></summary>

```bash
# Download EVE-NG Community ISO/OVA from:
# https://www.eve-ng.net/index.php/download/

# Or use wget (check for latest version)
wget https://www.eve-ng.net/download/eve-ng-community.ova
```

</details>

<details>
<summary><b>2. Initial Setup After Boot</b></summary>

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
<summary><b>3. Update EVE-NG</b></summary>

```bash
# Update system packages
apt update && apt upgrade -y

# Fix any broken packages
apt --fix-broken install
```

</details>

<details>
<summary><b>4. Access Web Interface</b></summary>

```bash
# Find your EVE-NG IP address
ip addr show

# Or
hostname -I

# Access in browser:
# http://YOUR-EVE-NG-IP

# Default web credentials:
# Username: admin
# Password: eve
```

</details>

<details>
<summary><b>5. Install Windows Client Pack (Optional)</b></summary>

```bash
# Download from EVE-NG website
# Windows Integration Pack includes:
# - Wireshark integration
# - PuTTY/SecureCRT integration
# - VNC viewer
# - RDP client
```

</details>

<details>
<summary><b>6. Upload Device Images</b></summary>

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
<summary><b>7. Useful EVE-NG Commands</b></summary>

```bash
# Check EVE-NG service status
systemctl status eve-ng

# Restart EVE-NG services
systemctl restart eve-ng

# Fix permissions (run after adding images)
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions

# Check running labs
eve-ng ps

# Stop all running nodes
/opt/unetlab/wrappers/unl_wrapper -a stopall

# View logs
tail -f /var/log/syslog
```

</details>

### 🖥️ Creating Your First Lab

1. **Login** to EVE-NG web interface
2. **Create New Lab**: Click `Add new lab` → Enter lab name
3. **Add Nodes**: Right-click → `Node` → Select device type
4. **Connect Devices**: Click on node interface → Drag to another node
5. **Start Nodes**: Select all → Right-click → `Start`
6. **Access Console**: Double-click on node to open console

### 📁 Project Structure

```
video-01/
├── README.md
├── lab-topology.png
└── configs/
    ├── R1-initial.cfg
    ├── R2-initial.cfg
    └── SW1-initial.cfg
```

### 🔗 Resources

- [EVE-NG Official Website](https://www.eve-ng.net/)
- [EVE-NG Documentation](https://www.eve-ng.net/index.php/documentation/)
- [EVE-NG Community Forum](https://www.eve-ng.net/forum/)
- [EVE-NG Cookbook](https://www.eve-ng.net/index.php/documentation/howtos/)

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
| Fortinet Docs | [docs.fortinet.com](https://docs.fortinet.com/) |

---

## 🤝 Connect With Me

<p align="center">
  <a href="https://youtube.com/@NetworkCoder"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube"></a>
  <a href="https://linkedin.com/in/YourProfile"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://twitter.com/YourHandle"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="Twitter"></a>
</p>

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  ⭐ <strong>If you find this helpful, please star the repo!</strong> ⭐
</p>
]]>
