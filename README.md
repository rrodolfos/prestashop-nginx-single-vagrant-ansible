# Configuring prestashop in a single server with ansible
This repository (https://github.com/rrodolfos/prestashop-nginx-single-vagrant-ansible.git) contains vagrant and ansible configuration to deploy and provision a single PrestaShop server with mysql (mariadb), nginx and php (fpm):

  - [Prestashop](https://www.prestashop.com/)
  - [MariaDB](https://mariadb.org/) or ~~[MySQL](https://www.mysql.com/)~~
  - [NGINX](https://www.nginx.org/)
  - [php](https://www.php.net/)

## DISCLAIMER
> This implementation is intended for testing / PoC / educational purposes only, this solution is not scalable or secure enough for live / production environments. Use it at your own risk. Have fun!.

## Requirements
The below requirements are needed to deploy and provision PrestaShop VM.

  - [VirtualBox](https://www.virtualbox.org/)
  - [Vagrant](https://www.vagrantup.com/)
  - [Ansible](https://www.ansible.com/)
  - [MySQL collection for Ansible](https://docs.ansible.com/ansible/latest/collections/community/mysql/index.html)

## what did I use for this?
  - MacBook Pro 2015 CPU Core i5 8GB RAM
  - OS GNU Linux/Debian 12 Bookworm 64bits
  - VirtualBox 6.1.32
  - Vagrant 2.2.19
    - Vagrant box debian/bullseye64
  - Ansible 2.12.3
  - MySQL collection for Ansible 2.1.0

## Included content
  - Vagrantfile
  - ansible.cfg
  - Collections
    - mysql
  - Playbook.yml
  - Roles
    - common
    - prestashop

### Vagrantfile
VM machine definition as follow:
  - prestashop
    - 2 vcpu
    - 1024 RAM
    - 192.168.33.13 VM ip address

## Architecture
![Architecture Diagram](https://raw.githubusercontent.com/rrodolfos/prestashop-nginx-single-vagrant-ansible/main/architecture/prestashop_single.webp "Architecture Diagram")

## How to build it

### Prestashop
This VM deploy a single PrestaShop server with mariadb, nginx and php as follow (by ansible):
  - Install php
  - Install MariaDB
    - Create prestashop database
	- Create prestashop user and its privileges
  - Install NGINX
    - Download and install prestashop
	- Configure NGINX prestashop server
  - Print prestashop URL
  - Have fun!

### Clone this repository
```
  $ git clone https://github.com/rrodolfos/prestashop-nginx-single-vagrant-ansible.git
```

### Change to the cloned repository directory
```
  $ cd prestashop-nginx-single-vagrant-ansible
```

### Create vagrant VM and deploy PrestaShop
To start up the VM
```
  $ vagrant up
```
> Coffee time!. On a MacBook Pro 2015 and 50Mbps bandwidth it took ~6 minutes. Vagrant box (base linux distro) downloading time not included.

### Check the VM
To connect to the VM (ssh)
```
  $ vagrant ssh
```

### Connect to PrestaShop
#### Shop
```
  http://prestashop.local
```

#### To connect as a customer via web browser
```
  http://prestashop.local/en/login
```
  `Username:` pub@prestashop.com
  `Password:` 123456789

#### To connect as a administrator (employee) via web browser
```
  http://prestashop.local/admin56
```
  `Username:` john.doe@foo.foo
  `Password:` 0123456789

### Destroy vagrant VM
To destroy the VM
```
  $ vagrant destroy
```
## Notes
  - Be sure the VM has the package ```acl``` is installed (Ansible should do it for you ;-)
  - To change paths, user names, passwords and prestashop installation values check:
    ```prestashop-nginx-single-vagrant-ansible/provisioning/roles/prestashop/vars/main.yml```
  - Please feel free to let me know any question, error, improvement or opinion by email

## Author

> Rodolfo Sauce-Guinand - rrodolfos gmail com
