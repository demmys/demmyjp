demmyjp
=====

This is the repository to manage demmy.jp server inflastructure, service and web pages.

# Requirements

* pyenv and virtualenv (or Python 3.X environment) on host machine ([anyenv](https://github.com/riywo/anyenv) is recommended)
* modern version of Ubuntu on remote machine

# Host machine installation

### 1. Clone repository

```bash
git clone git@github.com:demmys/demmyjp.git
cd demmyjp
```

### 2. Install Ansible

```bash
pyenv install 3.X.Y # install latest 3.X version of Python
pyenv virtualenv 3.X.Y ansible-3.X.Y
pyenv local ansible-3.X.Y
pip install ansible
pyenv rehash
```

### 3. Setup hosts

```bash
cp hosts.sample hosts
vim hosts # edit for your hosts
ansible all -i hosts -m ping
```

### 4. Set up variables

```bash
vim group_vars/webservers.yml # edit or add your variables to override defaults
```

# Execution

```bash
ansible-playbook -i hosts site.yml --ask-sudo-pass
```
