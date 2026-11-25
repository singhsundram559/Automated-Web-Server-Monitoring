# Automated Web Server Configuration and Monitoring

## Project Overview
This project automates web server configuration and monitors website availability using Ansible and Nagios Core.

## Objectives
- Automate Nginx installation using Ansible.
- Deploy a static website.
- Monitor HTTP availability using Nagios.
- Detect web server failures.
- Verify service recovery.
- Demonstrate Ansible idempotency.

## Technologies Used
- Ubuntu 24.04 LTS (WSL2)
- Ansible
- Nagios Core 4.4.6
- Nginx
- Apache2
- SSH
- HTML and CSS

## Architecture
This implementation uses one Ubuntu WSL2 environment.

- Ansible configures Nginx locally.
- Nginx hosts the website on port 80.
- Nagios monitors the HTTP service.
- Apache2 hosts the Nagios dashboard on port 8081.
- SSH runs on port 22.

## Project Structure
- ansible/ — Ansible inventory, configuration and playbook
- website/ — HTML and CSS files
- nagios/ — Nagios configuration files
- documentation/ — Project documentation
- screenshots/ — Project evidence

## Execution Steps

1. Open the Ansible directory:
   cd ~/Automated-Web-Server-Monitoring/ansible

2. Test connectivity:
   ansible webservers -m ping

3. Deploy the web server:
   ansible-playbook deploy.yml -K

4. Verify Nginx:
   sudo systemctl status nginx

5. Open the website:
   http://localhost

6. Open the Nagios dashboard:
   http://localhost:8081/nagios4/

## Testing
- Ansible connectivity test
- Nginx deployment test
- Idempotency test
- HTTP availability test
- Nginx failure detection
- Service recovery test

## Implementation Note
This is a local single-node WSL2 implementation. Separate virtual machines and cloud-hosted servers are not used.

## Author
Sundram Singh

## Course
INT333 - Fundamentals of DevOps
