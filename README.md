Here's the complete Wazuh Home Lab setup guide in a single, well-formatted markdown file:


# 🚀 Wazuh Home Lab Setup

## Table of Contents
- [Overview](#-overview)
- [Prerequisites](#-prerequisites)
- [Installation Guide](#️-installation-guide)
  - [Part 1: Wazuh Manager Deployment](#part-1-wazuh-manager-deployment)
  - [Part 2: Wazuh Agent Integration](#part-2-wazuh-agent-integration)
- [Adversary Emulation](#-adversary-emulation)
- [References](#-references)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔍 Overview

The Wazuh Home Lab provides hands-on experience with Wazuh's security capabilities:

- Real-time threat detection and response
- Endpoint monitoring and analysis
- SIEM and XDR functionality
- Adversary emulation for testing defenses

---

## 📋 Prerequisites

### Hardware Requirements
- Virtualization: VMware/VirtualBox
- Wazuh Manager:
  - 4GB RAM minimum
  - 2 CPU cores
  - 50GB storage
- Endpoints: 2GB RAM each

### Software Requirements
- Ubuntu Server 20.04 LTS
- Internet access for package installation
- SSH access configured

---

## ⚙️ Installation Guide

### Part 1: Wazuh Manager Deployment

1. **System Preparation**

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl apt-transport-https unzip wget libcap2-bin \
software-properties-common lsb-release gnupg2
```

2. **Repository Setup**
```bash
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo apt-key add -
echo "deb https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
```

3. **Installation**
```bash
sudo apt update
sudo apt install -y wazuh-manager
sudo systemctl enable --now wazuh-manager
```

4. **Verification**
```bash
sudo systemctl status wazuh-manager
journalctl -u wazuh-manager -f
```

### Part 2: Wazuh Agent Integration

1. **Agent Installation (Linux)**
```bash
sudo apt install -y wazuh-agent
```

2. **Agent Configuration**
```bash
sudo nano /var/ossec/etc/ossec.conf
```
Set manager IP:
```xml
<client>
  <server-ip>MANAGER_IP</server-ip>
</client>
```

3. **Agent Registration**
```bash
sudo /var/ossec/bin/manage_agents
```
Select option to add agent and follow prompts

4. **Service Management**
```bash
sudo systemctl enable --now wazuh-agent
sudo systemctl status wazuh-agent
```

---

## 💻 Adversary Emulation

### Atomic Red Team Setup
```bash
git clone https://github.com/redcanaryco/atomic-red-team.git
cd atomic-red-team
./install.sh
```

### Sample Test Execution
```bash
atomic-red-team execute --atomic-test-id T1059.004
```

### Common Test Scenarios
1. Persistence:
```bash
atomic-red-team execute --atomic-test-id T1547.001
```
2. Discovery:
```bash
atomic-red-team execute --atomic-test-id T1087
```
3. Execution:
```bash
atomic-red-team execute --atomic-test-id T1059
```

---

## 📚 References
- [Official Wazuh Documentation](https://documentation.wazuh.com/)
- [Atomic Red Team GitHub](https://github.com/redcanaryco/atomic-red-team)
- [MITRE ATT&CK Framework](https://attack.mitre.org/)

---

## 🤝 Contributing
1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a pull request

---

## 📝 License
MIT License - See [LICENSE](LICENSE) for details

---

## 👨‍💻 About
Created by [Adil Javed](https://medium.com/@AdiljavedOffical)  
For more cybersecurity content visit:  
[Medium Profile](https://medium.com/@AdiljavedOffical) | 
[GitHub](https://github.com/yourprofile)

---

### Stay Secure! 🔐

This single-file version includes:
1. All original content consolidated
2. Proper markdown formatting
3. Improved code block organization
4. Consistent heading levels
5. Additional verification steps
6. Expanded adversary emulation examples
7. Better section linking
8. Complete installation and configuration details
