# Internship Project - Ansible Playbook

## Overview
This Ansible playbook automates the setup of a LEMP (Linux, Nginx, MySQL, PHP) stack, VSFTPD for FTP access, and phpMyAdmin for database management. The playbook is designed to work on Ubuntu-based systems.

## Features
- Installs required packages: Nginx, MariaDB, PHP 8.1, and additional PHP modules.
- Enables and starts necessary services.
- Secures MariaDB using `mysql_secure_installation`.
- Creates a user `dani` with secure password hashing.
- Configures FTP access using VSFTPD with SSL encryption.
- Downloads and sets up phpMyAdmin.
- Installs `pip3` and `pymysql` for MySQL Python integration.

## Requirements
- Ubuntu-based system
- Python 3
- Ansible installed

## Usage
### Step 1: Install Ansible
If Ansible is not installed, run:
```bash
sudo apt update && sudo apt install ansible -y
```

### Step 2: Run the Playbook
Execute the following command:
```bash
ansible-playbook -i inventory ansible.yml
```
Replace `inventory` with your actual inventory file containing the target hosts.

## Playbook Breakdown
### 1. Installing Packages
The playbook installs:
- Nginx (Web server)
- MariaDB (Database server)
- PHP 8.1 and required extensions
- VSFTPD (FTP server)
- Unzip (For extracting phpMyAdmin)
- Python packages (`pymysql`)

### 2. Configuring Services
- Enables and starts `nginx`, `mariadb`, `php8.1-fpm`, and `vsftpd`.
- Configures MariaDB securely.
- Configures VSFTPD with SSL and user restrictions.

### 3. Setting Up User and Directory Permissions
- Creates a new user `dani` with a hashed password.
- Creates a web directory `/home/dani/myweb/public`.
- Configures VSFTPD to allow `dani` to upload files securely.

### 4. Installing phpMyAdmin
- Downloads and extracts the latest phpMyAdmin version.
- Moves it to `/var/www/phpmyadmin` and assigns proper permissions.

## Notes
- Ensure Ansible has root privileges (`become: yes`).
- Modify `vars` in `ansible.yml` if necessary.
- For troubleshooting, check Ansible logs using `-vvv` flag.

## License
This project is licensed under the MIT License.

## Author
**Daniels Pericorn**

