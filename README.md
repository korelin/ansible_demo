## ansible demo
Step 0 - Create User
```shell
sudo adduser ansible
sudo usermod -aG sudo ansible
su - ansible
ssh-keygen
cat ~/.ssh/id_rsa.pub
```
Step 1 — Installing Ansible

```shell
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible
```
Step 2 — Setting Up the Inventory File

```shell
sudo vi /etc/ansible/hosts
```
File example:
```
[servers]
server1 ansible_host=203.0.113.111
server2 ansible_host=203.0.113.112
server3 ansible_host=203.0.113.113

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

```shell
ansible-inventory --list -y
```
Step 3 — Testing Connection

```shell
ansible all -m ping
```

Step 4 — Running Ad-Hoc Commands (Optional)
```shell
ansible all -a "df -h"
ansible all -a "hostname"
ssh <host> hostname
ansible servers -a "uptime"
ansible server1:server2 -m ping
```