demmyjp
=====

This is the repository to manage demmy.jp server inflastructure, service and web pages.

# Requirements

* pyenv and virtualenv (or Python 2.X environment) on host machine
* modern version of Ubuntu on remote machine

# Host machine installation

### 1. Clone repository

```bash
git clone git@github.com:demmys/demmyjp.git
cd demmyjp
```

### 2. Install Ansible

```bash
pyenv install 2.X.Y # install latest 2.X version of Python
pyenv virtualenv 2.X.Y ansible-2.X.Y
pyenv local ansible-2.X.Y
pip install ansible
pyenv rehash
```

### 3. Setup hosts

```bash
cp hosts.sample hosts
vim hosts # edit for your hosts
ansible all -i hosts -m ping
```

### 4. Set SSL certificate

```bash
cp /your/path/to/ssl.crt roles/index/files/demmy_jp.crt
cp /your/path/to/ssl.key roles/index/files/demmy_jp.key
```

### 5. Set variables (if needed)

```bash
mkdir group_vars
vim group_vars/webservers.yml # set your variables
```

# Execution

```bash
ansible-playbook -i hosts site.yml --ask-sudo-pass
```
