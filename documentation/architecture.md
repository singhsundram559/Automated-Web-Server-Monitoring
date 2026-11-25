# Project Architecture

## 1. Overview
The project implements automated web server configuration and monitoring using Ansible and Nagios Core in a single Ubuntu WSL2 environment.

## 2. Architecture Components

### Ansible
- Acts as the configuration management tool.
- Installs Nginx.
- Deploys website HTML and CSS files.
- Ensures the Nginx service is running.

### Nginx
- Hosts the static project website.
- Listens on port 80.
- Serves the website at http://localhost.

### Nagios Core
- Monitors the Nginx HTTP service.
- Checks website availability.
- Reports OK and CRITICAL service states.

### Apache2
- Hosts the Nagios web dashboard.
- Uses port 8081.

### SSH
- SSH service runs on port 22.
- Provides SSH service availability for monitoring.

## 3. Request and Monitoring Flow

1. Ansible executes the deployment playbook.
2. Nginx is installed and configured.
3. Website files are copied to the Nginx web directory.
4. Nginx serves the website on port 80.
5. Nagios checks HTTP availability.
6. If Nginx stops, Nagios reports CRITICAL.
7. After Nginx restarts, Nagios reports OK again.

## 4. Environment
- Operating System: Ubuntu 24.04 LTS
- Platform: Windows Subsystem for Linux 2 (WSL2)
- Deployment Model: Single-node local implementation
- Web Server Port: 80
- Nagios Dashboard Port: 8081
- SSH Port: 22

## 5. Architecture Limitation
This implementation uses one local WSL2 environment. Ansible and Nagios are not deployed on separate virtual machines.
