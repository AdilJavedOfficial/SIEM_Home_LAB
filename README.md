# Wazuh Home Lab Setup

![Wazuh Logo](https://wazuh.com/wp-content/uploads/2019/03/wazuh_logo_color.png)

This repository provides a step-by-step guide to setting up a Wazuh Home Lab for advanced threat detection and response. The setup includes deploying the Wazuh manager, integrating agents, and utilizing adversary emulation tools to enhance your cybersecurity skills.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation Guide](#installation-guide)
  - [Part 1: Deploying the Wazuh Manager](#part-1-deploying-the-wazuh-manager)
  - [Part 2: Integrating Wazuh Agents](#part-2-integrating-wazuh-agents)
- [Adversary Emulation](#adversary-emulation)
- [References](#references)
- [Contributing](#contributing)
- [License](#license)

## Overview

The Wazuh Home Lab is designed to provide hands-on experience with the Wazuh security platform, offering unified XDR (Extended Detection and Response) and SIEM (Security Information and Event Management) capabilities. This lab setup allows you to monitor endpoints, detect threats, and respond to security incidents effectively.

## Prerequisites

Before proceeding with the installation, ensure you have the following:

- A virtualized environment (e.g., VMware, VirtualBox) to host the Wazuh components.
- Ubuntu Server 20.04 LTS installed on the virtual machines.
- Sufficient system resources: at least 4 GB RAM and 2 CPU cores for the Wazuh manager.

## Installation Guide

### Part 1: Deploying the Wazuh Manager

1. **Update the System**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Required Packages**:
   ```bash
   sudo apt install curl apt-transport-https unzip wget libcap2-bin software-properties-common lsb-release gnupg2 -y
   ```

3. **Add Wazuh Repository**:
   ```bash
   curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo apt-key add -
   echo "deb https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
   ```

4. **Install the Wazuh Manager**:
   ```bash
   sudo apt update
   sudo apt install wazuh-manager -y
   ```

5. **Start and Enable the Wazuh Manager**:
   ```bash
   sudo systemctl enable --now wazuh-manager
   ```

### Part 2: Integrating Wazuh Agents

1. **Install the Wazuh Agent on Endpoints**:
   - Download the agent package suitable for your operating system from the [Wazuh downloads page](https://wazuh.com/downloads/).
   - Install the agent using the appropriate method for your OS.

2. **Configure the Agent to Communicate with the Manager**:
   - Edit the agent configuration file (e.g., `ossec.conf`) to set the manager's IP address.
   - Register the agent with the manager using the `manage_agents` utility.

3. **Start and Enable the Wazuh Agent**:
   ```bash
   sudo systemctl enable --now wazuh-agent
   ```

## Adversary Emulation

To enhance the lab's capabilities, you can integrate adversary emulation tools like Atomic Red Team:

- **Deploying Atomic Red Team**:
  - Clone the Atomic Red Team repository:
    ```bash
    git clone https://github.com/redcanaryco/atomic-red-team.git
    ```
  - Navigate to the cloned directory and follow the setup instructions provided in the repository.

## References

- [Wazuh HomeLab Installation Guide Part 1](https://medium.com/@AdiljavedOffical/wazuh-homelab-installtion-guide-part-1-6d6b5f3b8f2e)
- [Wazuh HomeLab Installation Guide Part 2](https://medium.com/@AdiljavedOffical/wazuh-homelab-installtion-guide-part-2-6d6b5f3b8f2e)
- [Deploying Atomic Red Team for Adversary Emulation](https://medium.com/@AdiljavedOffical/deploying-atomic-red-team-for-adversary-emulation-4d5a5f3b8f2e)

## Contributing

Contributions are welcome! If you'd like to enhance this project, please fork the repository, make your changes, and submit a pull request.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

*This README is based on guides and tutorials authored by [Adil Javed](https://medium.com/@AdiljavedOffical). For more insightful articles on cybersecurity and threat detection, visit his [Medium profile](https://medium.com/@AdiljavedOffical).*

