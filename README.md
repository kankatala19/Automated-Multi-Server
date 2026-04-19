# Automated Multi-Server Infrastructure Setup using Ansible

## Overview

This project demonstrates how to automate the provisioning and configuration of multiple Linux servers using Ansible. A local control node manages two remote target servers and installs required software such as Docker and Nginx through reusable playbooks and roles.

The goal of this project is to reduce manual server setup, maintain consistent configurations, and apply DevOps automation practices.

---

## Architecture

```text
Control Node (Laptop / Local Machine)
        |
        | SSH
        v
---------------------------------
| Target Server 1 (Linux/EC2)   |
| - Docker                      |
| - Nginx                       |
---------------------------------
| Target Server 2 (Linux/EC2)   |
| - Docker                      |
| - Nginx                       |
---------------------------------
```

---

## Tools & Technologies

* Ansible
* Linux
* Amazon EC2
* Docker
* Nginx
* GitHub
* SSH

---

## Features

* Centralized management of multiple servers
* Passwordless SSH authentication
* Automated package installation
* Docker installation and setup
* Nginx installation and service enablement
* Reusable Ansible roles
* Easy scaling to additional servers

---

## Project Structure

```text
Automated-Multi-Server/
├── inventory.ini
├── site.yml
├── roles/
│   ├── common/
│   │   └── tasks/main.yml
│   ├── docker/
│   │   └── tasks/main.yml
│   └── nginx/
│       └── tasks/main.yml
└── README.md
```

---

## Inventory Example

```ini
[webservers]
server1-ip
server2-ip

[webservers:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/key.pem
```

---

## Main Playbook

```yaml
- hosts: webservers
  become: true
  roles:
    - common
    - nginx
    - docker
```

---

## How to Run

### 1. Clone Repository

```bash
git clone https://github.com/kankatala19/Automated-Multi-Server.git
cd Automated-Multi-Server
```

### 2. Update Inventory

Add your target server IP addresses and SSH details in `inventory.ini`.

### 3. Test Connectivity

```bash
ansible all -i inventory.ini -m ping
```

### 4. Execute Playbook

```bash
ansible-playbook -i inventory.ini site.yml
```

---

## What I Learned

* Linux server management
* SSH key-based authentication
* Infrastructure automation
* Ansible inventories, playbooks, and roles
* Multi-server configuration management
* DevOps best practices
