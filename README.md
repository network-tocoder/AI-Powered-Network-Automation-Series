# 🚀 Network Automation Series

![Network Coder Banner](assets/banner.jpg)

**Network | AI | Tool Integration | Virtual LAB | Automation**

[![YouTube](https://img.shields.io/badge/YouTube-NetworkCoder-red?style=for-the-badge&logo=youtube)](https://youtube.com/@NetworkCoder)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=for-the-badge&logo=github)](https://github.com/network-tocoder)

---

## 🎓 What You'll Learn

This series takes you from zero to hero in network automation. Build a complete virtual lab, automate firewalls, deploy NetBox for infrastructure management, and integrate everything with modern DevOps tools.

---

## 📺 Video Index

| # | Video | Topic | YouTube |
|---|-------|-------|---------|
| 1 | [EVE-NG Installation](#video-1-eve-ng-installation--virtual-lab-setup) | EVE-NG, Virtual Lab Setup | [▶️ Watch](https://www.youtube.com/watch?v=ABNOS7GypxA) |
| 2 | [Build Automation Environment](#video-2-build-automation-environment-inside-eve-ng) | Linux, Ansible, VS Code | [▶️ Watch](https://www.youtube.com/watch?v=NPq7AjCguBY) |
| 3 | [Git Workflow](#video-3-git-workflow-for-network-engineers) | Git, GitHub, Version Control | [▶️ Watch](https://www.youtube.com/watch?v=VIDEO-3-ID) |
| 4 | [Deploy FortiGate](#video-4-deploy-fortigate-firewall-on-eve-ng) | FortiGate, EVE-NG | [▶️ Watch](https://www.youtube.com/watch?v=8W9OJAP773s) |
| 5 | [FortiGate + Ansible](#video-5-fortigate-automation-using-ansible) | Ansible, Vault, Playbooks | [▶️ Watch](https://www.youtube.com/watch?v=3VL-JRIJT8M) |
| 6 | [FortiGate + REST API](#video-6-fortigate-automation-using-rest-api) | REST API, Postman | [▶️ Watch](https://www.youtube.com/watch?v=Eqy4q9SsmtE) |
| 7 | [NetBox + Docker](#video-7-netbox-installation-using-docker) | NetBox, Docker Compose | [▶️ Watch](https://www.youtube.com/watch?v=OGQGly7NIFY) |
| 8 | [NetBox Dynamic Inventory](#video-8-netbox-dynamic-inventory---core-concepts) | ORB, DIODE, Architecture | [▶️ Watch](https://www.youtube.com/watch?v=JZ-jDCT8mQY) |
| 9 | [NetBox Auto-Discovery](#video-9-netbox-auto-discovery---complete-setup-guide) | DIODE, ORB Agent, OAuth | [▶️ Watch](https://www.youtube.com/watch?v=DODzEsMTmKQ) |
| 10 | [pyATS + NetBox](#video-10-pyats--netbox-integration) | pyATS, Network Testing | [▶️ Watch](https://www.youtube.com/watch?v=V_PmWxC2QDA) |

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

## Video 1: EVE-NG Installation & Virtual Lab Setup

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=ABNOS7GypxA)

### 📋 Overview

Install EVE-NG on VMware Workstation and build your first virtual network topology.

### 🎯 What You'll Learn

- Install EVE-NG on VMware Workstation
- Build your first virtual network topology
- Configure network devices for automation

### 💻 System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| CPU | 4 Cores (VT-x/AMD-V enabled) | 8+ Cores |
| RAM | 8 GB | 16+ GB |
| Storage | 50 GB | 100+ GB SSD |
| Hypervisor | VMware/VirtualBox | VMware Workstation Pro |

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

## Video 2: Build Automation Environment Inside EVE-NG

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=NPq7AjCguBY)

### 📋 Overview

Deploy a Linux node inside EVE-NG, install Ansible, and integrate VS Code for a professional automation workflow.

### 🎯 What You'll Learn

- Deploy Linux node in EVE-NG
- Install Ansible for network automation
- Integrate VS Code for professional workflow

### 💻 Commands

<details>
<summary>1. Install Ansible</summary>

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Ansible
sudo apt install ansible -y

# Verify installation
ansible --version
```

</details>

<details>
<summary>2. Install Python & pip</summary>

```bash
# Install Python and pip
sudo apt install python3 python3-pip -y

# Verify installation
python3 --version
pip3 --version
```

</details>

<details>
<summary>3. VS Code Remote SSH Setup</summary>

```bash
# Install OpenSSH Server on Linux node
sudo apt install openssh-server -y

# Start SSH service
sudo systemctl start ssh
sudo systemctl enable ssh

# Check SSH status
sudo systemctl status ssh

# Get IP address for VS Code connection
ip addr show
```

</details>

### 🔗 Resources

- [Ansible Installation Guide](https://docs.ansible.com/ansible/latest/installation_guide/)
- [VS Code Remote SSH](https://code.visualstudio.com/docs/remote/ssh)

---

## Video 3: Git Workflow for Network Engineers

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=VIDEO-3-ID)

### 📋 Overview

Learn Git version control essentials and push your Ansible projects to GitHub.

### 🎯 What You'll Learn

- Complete Git workflow explained
- Push Ansible projects to GitHub
- Version control for network automation

### 💻 Commands

<details>
<summary>1. Install & Configure Git</summary>

```bash
# Install Git
sudo apt install git -y

# Configure Git
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify configuration
git config --list
```

</details>

<details>
<summary>2. Initialize Repository</summary>

```bash
# Initialize new repository
git init

# Add all files
git add .

# First commit
git commit -m "Initial commit"
```

</details>

<details>
<summary>3. Push to GitHub</summary>

```bash
# Add remote origin
git remote add origin https://github.com/username/repo.git

# Push to main branch
git push -u origin main
```

</details>

<details>
<summary>4. Common Git Commands</summary>

```bash
# Check status
git status

# View commit history
git log --oneline

# Create new branch
git checkout -b feature-branch

# Merge branch
git merge feature-branch

# Pull latest changes
git pull origin main
```

</details>

### 🔗 Resources

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)

---

## Video 4: Deploy FortiGate Firewall on EVE-NG

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=8W9OJAP773s)

### 📋 Overview

Install and configure FortiGate firewall in your EVE-NG virtual lab.

### 🎯 What You'll Learn

- FortiGate installation in virtual lab
- Network security device configuration
- Integration with automation stack

### 💻 Commands

<details>
<summary>1. Upload FortiGate Image</summary>

```bash
# Upload FortiGate qcow2 image via SFTP to:
/opt/unetlab/addons/qemu/fortinet-FGT/

# Fix permissions
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions
```

</details>

<details>
<summary>2. FortiGate Initial Configuration</summary>

```bash
# Default credentials
Username: admin
Password: (blank - press Enter)

# Set new password
config system admin
    edit admin
        set password YourNewPassword
    next
end

# Configure management interface
config system interface
    edit port1
        set ip 192.168.1.111/24
        set allowaccess ping https ssh http
    next
end
```

</details>

<details>
<summary>3. Enable API Access</summary>

```bash
# Create API admin user
config system api-user
    edit "api-admin"
        set accprofile "super_admin"
        set vdom "root"
        config trusthost
            edit 1
                set ipv4-trusthost 192.168.1.0/24
            next
        end
    next
end

# Generate API token (from GUI)
# System > Administrators > api-admin > Regenerate
```

</details>

### 🔗 Resources

- [FortiGate Documentation](https://docs.fortinet.com/product/fortigate)
- [EVE-NG FortiGate Setup](https://www.eve-ng.net/index.php/documentation/howtos/)

---

## Video 5: FortiGate Automation Using Ansible

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=3VL-JRIJT8M)

### 📋 Overview

Automate FortiGate firewalls using Ansible with secure credential storage via Ansible Vault.

### 🎯 What You'll Learn

- Install Ansible Collections for FortiGate
- Ansible Vault Setup
- Demo Playbook 1 - System Information Check
- Demo Playbook 2 - Deploy Firewall Policy

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

## Video 6: FortiGate Automation Using REST API

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=Eqy4q9SsmtE)

### 📋 Overview

Automate FortiGate using REST API with Postman and VS Code integration.

### 🎯 What You'll Learn

- REST API automation with Postman
- VS Code integration for API testing
- GitHub workflow for firewall configs

### 💻 Commands

<details>
<summary>1. Get System Status (cURL)</summary>

```bash
# Get system status
curl -k -X GET "https://192.168.1.111/api/v2/monitor/system/status" \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

</details>

<details>
<summary>2. Get Firewall Policies</summary>

```bash
# List all firewall policies
curl -k -X GET "https://192.168.1.111/api/v2/cmdb/firewall/policy" \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

</details>

<details>
<summary>3. Create Firewall Policy</summary>

```bash
# Create new policy
curl -k -X POST "https://192.168.1.111/api/v2/cmdb/firewall/policy" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Allow-Web",
    "srcintf": [{"name": "port1"}],
    "dstintf": [{"name": "port2"}],
    "srcaddr": [{"name": "all"}],
    "dstaddr": [{"name": "all"}],
    "service": [{"name": "HTTP"}, {"name": "HTTPS"}],
    "action": "accept",
    "status": "enable"
  }'
```

</details>

### 🔗 Resources

- [FortiGate REST API Guide](https://docs.fortinet.com/document/fortigate/7.0.0/administration-guide/940602/rest-api)
- [Postman Download](https://www.postman.com/downloads/)

---

## Video 7: NetBox Installation Using Docker

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=OGQGly7NIFY)

### 📋 Overview

Deploy NetBox with Docker Compose for IPAM and DCIM management.

### 🎯 What You'll Learn

- Deploy NetBox with Docker Compose
- Complete setup and configuration
- Prepare for auto-discovery integration

### 💻 Commands

<details>
<summary>1. Install Docker</summary>

```bash
# Install Docker + Docker Compose
sudo apt install -y docker.io docker-compose

# Start Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add user to docker group
sudo usermod -aG docker $USER

# Verify installation
docker --version
docker-compose --version
```

</details>

<details>
<summary>2. Download & Configure NetBox</summary>

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
<summary>3. Start NetBox</summary>

```bash
# Pull images
docker-compose pull

# Start NetBox stack
docker-compose up -d

# Check status
docker-compose ps

# Verify port listening
ss -tuln | grep :8000
```

</details>

<details>
<summary>4. Troubleshooting</summary>

```bash
# View logs
docker-compose logs
docker-compose logs netbox

# Restart NetBox
docker-compose restart netbox

# Nuclear reset (removes all data!)
docker-compose down -v
docker-compose pull
docker-compose up -d
```

</details>

<details>
<summary>5. Create Superuser</summary>

```bash
docker-compose exec netbox /opt/netbox/netbox/manage.py createsuperuser
```

</details>

### 🔗 Resources

- [NetBox Documentation](https://docs.netbox.dev/)
- [NetBox Docker GitHub](https://github.com/netbox-community/netbox-docker)

---

## Video 8: NetBox Dynamic Inventory - Core Concepts

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=JZ-jDCT8mQY)

### 📋 Overview

Understand the architecture of auto-discovery stack with ORB, DIODE, and NetBox.

### 🎯 What You'll Learn

- Architecture overview of auto-discovery stack
- How ORB, DIODE, and NetBox work together
- Understanding the data flow

### 🏗️ Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Network    │     │    ORB      │     │   DIODE     │
│  Devices    │────▶│   Agent     │────▶│   Server    │
└─────────────┘     └─────────────┘     └─────────────┘
                                              │
                                              ▼
                                        ┌─────────────┐
                                        │   NetBox    │
                                        │   (DCIM)    │
                                        └─────────────┘
```

### 🔗 Resources

- [NetBox DIODE Plugin](https://github.com/netboxlabs/diode-netbox-plugin)
- [ORB Agent Documentation](https://github.com/netboxlabs/orb-agent)

---

## Video 9: NetBox Auto-Discovery - Complete Setup Guide

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=DODzEsMTmKQ)

### 📋 Overview

Complete setup guide for NetBox auto-discovery with DIODE and ORB Agent.

### 🎯 What You'll Learn

- Deploy DIODE Server with Docker
- Install and configure NetBox DIODE Plugin
- Setup ORB Agent with OAuth authentication
- Troubleshoot common issues
- Live auto-discovery demonstration

### 💻 Commands

<details>
<summary>1. Deploy DIODE Server</summary>

```bash
# Clone DIODE repository
git clone https://github.com/netboxlabs/diode.git
cd diode

# Start DIODE with Docker Compose
docker-compose up -d

# Verify DIODE is running
docker-compose ps
```

</details>

<details>
<summary>2. Install NetBox DIODE Plugin</summary>

```bash
# Add to NetBox docker-compose.override.yml
# Under netbox service, add:
#   PLUGINS: "netbox_diode"

# Restart NetBox
docker-compose restart netbox
```

</details>

<details>
<summary>3. Configure ORB Agent</summary>

```bash
# Download ORB Agent
# Configure orb-agent.yaml with:
# - NetBox URL
# - DIODE Server URL
# - OAuth credentials
# - Target network devices

# Start ORB Agent
./orb-agent run -c orb-agent.yaml
```

</details>

### 🔗 Resources

- [DIODE GitHub](https://github.com/netboxlabs/diode)
- [NetBox DIODE Plugin](https://github.com/netboxlabs/diode-netbox-plugin)

---

## Video 10: pyATS + NetBox Integration

[▶️ Watch on YouTube](https://www.youtube.com/watch?v=V_PmWxC2QDA)

### 📋 Overview

Network testing with pyATS and automated inventory sync with NetBox.

### 🎯 What You'll Learn

- Network testing with pyATS
- Automated inventory sync
- Integration workflow

### 💻 Commands

<details>
<summary>1. Install pyATS</summary>

```bash
# Create virtual environment
python3 -m venv pyats-env
source pyats-env/bin/activate

# Install pyATS
pip install pyats[full]

# Verify installation
pyats version check
```

</details>

<details>
<summary>2. Create Testbed File</summary>

```yaml
# testbed.yaml
testbed:
  name: Network-Lab

devices:
  router1:
    os: ios
    type: router
    connections:
      defaults:
        class: unicon.Unicon
      ssh:
        protocol: ssh
        ip: 192.168.1.10
    credentials:
      default:
        username: admin
        password: cisco123
```

</details>

<details>
<summary>3. Run pyATS Tests</summary>

```bash
# Connect to device
pyats shell --testbed testbed.yaml

# Run a job
pyats run job my_job.py --testbed testbed.yaml

# Parse command output
pyats parse "show version" --testbed testbed.yaml --device router1
```

</details>

### 🔗 Resources

- [pyATS Documentation](https://developer.cisco.com/docs/pyats/)
- [pyATS GitHub](https://github.com/CiscoTestAutomation/pyats)

---

## 📚 Additional Resources

| Resource | Link |
|----------|------|
| EVE-NG | [eve-ng.net](https://www.eve-ng.net/) |
| NetBox | [netbox.dev](https://netbox.dev/) |
| Ansible Docs | [docs.ansible.com](https://docs.ansible.com/) |
| Docker Docs | [docs.docker.com](https://docs.docker.com/) |
| Fortinet Docs | [docs.fortinet.com](https://docs.fortinet.com/) |
| pyATS Docs | [developer.cisco.com/pyats](https://developer.cisco.com/docs/pyats/) |

---

## 🤝 Connect With Me

[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtube.com/@NetworkCoder)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/YourProfile)

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ **If you find this helpful, please star the repo!** ⭐
