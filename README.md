# Ansible Linux Baseline Configuration

## Overview

This project demonstrates the use of Ansible to automate baseline Linux server configuration across multiple Rocky Linux systems.

The goal was to standardize system configuration, improve security, deploy common services, and demonstrate infrastructure automation using Ansible. The project provisions administrative access, installs required packages, hardens SSH, configures the firewall, deploys a web server, and creates a dynamic Message of the Day (MOTD) using Ansible facts.

---

## Skills Demonstrated

- Ansible Automation
- Linux Administration
- Infrastructure as Code (IaC)
- SSH Hardening
- User Management
- Package Management
- Firewalld Administration
- NGINX Deployment
- Jinja2 Templating
- Variable Management
- Service Management
- Idempotent Configuration Management

---

## Environment

| Component | Value |
|------------|------------|
| Control Node | Rocky Linux 9 |
| Managed Nodes | Rocky Linux 9 |
| Automation Tool | Ansible |
| Web Server | NGINX |
| Firewall | firewalld |
| Configuration Method | Playbooks |
| Templating Engine | Jinja2 |

---

## Project Structure

```text
ansible/
├── ansible.cfg
├── inventory
├── site.yml
├── group_vars/
│   └── all.yml
├── templates/
│   └── motd.j2
└── playbooks/
    ├── users.yml
    ├── packages.yml
    ├── ssh.yml
    ├── firewall.yml
    ├── nginx.yml
    └── motd.yml
```

---

## Ansible Configuration

### Ansible Configuration File

Configured Ansible defaults including inventory location, privilege escalation, and execution settings.

Screenshot:

![Ansible Configuration](ansible_cfg.png)

---

### Inventory

Defined managed hosts used by the Ansible control node.

Screenshot:

![Inventory](inventory.png)

---

### Group Variables

Centralized reusable variables used throughout the project.

Variables include:

- Administrative username
- Common package list

Packages deployed:

- wget
- curl
- git
- nginx
- firewalld

Screenshot:

![Group Variables](group_vars.png)

---

## Main Playbook

A centralized playbook was created to orchestrate all configuration tasks.

Screenshot:

![Site Playbook](site_yml.png)

---

## Configuration Tasks

### User Management

Created a centralized administrative account and added it to the wheel group for sudo access.

Screenshot:

![Users Playbook](users_yml.png)

Verification:

![Sysadmin Verification](sysadmin_check.png)

---

### Package Installation

Installed common administration packages and required services.

Screenshot:

![Packages Playbook](packages_yml.png)

---

### SSH Hardening

Configured SSH security settings including:

- Disabled direct root login
- Configured ClientAliveInterval
- Configured ClientAliveCountMax
- Restarted SSH service automatically

Screenshot:

![SSH Playbook](ssh_yml.png)

Verification:

![SSH Verification](ssh_check.png)

---

### Firewall Configuration

Configured firewalld and ensured SSH and HTTP services were allowed.

Screenshot:

![Firewall Playbook](firewall_yml.png)

Verification:

![Firewall Verification](firewall_check.png)

---

### NGINX Deployment

Installed and enabled the NGINX web service.

Screenshot:

![NGINX Playbook](nginx_yml.png)

Verification:

![NGINX Verification](nginx_check.png)

---

### Dynamic MOTD Deployment

Created a Jinja2 template that generates a dynamic login banner using Ansible facts.

Template:

![MOTD Template](motd_j2.png)

Playbook:

![MOTD Playbook](motd_yml.png)

Verification:

![MOTD Verification](motd_check.png)

---

## Playbook Execution

Executed the site playbook against all managed nodes.

Screenshot:

![Playbook Results](results_yml.png)

---

## Idempotency Verification

Re-ran the playbook to verify idempotent behavior and ensure systems remained in the desired state.

Screenshot:

![Idempotency Check](idempotency_check.png)

---

## Results

The playbook successfully automated the following tasks across multiple Rocky Linux servers:

- Created administrative user accounts
- Installed common Linux packages
- Hardened SSH configuration
- Configured firewalld rules
- Deployed and enabled NGINX
- Generated a dynamic MOTD using Jinja2 templates
- Demonstrated idempotent Ansible automation

---

## Lessons Learned

Through this project I gained hands-on experience with:

- Organizing Ansible projects using playbooks and variables
- Managing Linux servers at scale
- Using Jinja2 templates to generate dynamic configuration files
- Implementing infrastructure automation workflows
- Verifying configuration compliance across multiple hosts
- Building repeatable and idempotent automation processes
