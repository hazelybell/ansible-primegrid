# Primegrid Ansible Script

This playbook installs, configures, and starts 
[primegrid](http://www.primegrid.com/)
via boinc-client on a remote system.

## Requirements

* Ansible

## Installation

```
git clone https://github.com/hazelybell/ansible-primegrid.git
cd ansible-primegrid
python3 -m virtualenv -p python3 venv
source venv/bin/activate
pip install ansible
```

## Configuration

To configure the script, put your weak account key in playbook.yml after
`weak_account_key: `.
You can get
the weak account key on the [Your Account](http://www.primegrid.com/home.php)
page on primegrid.

Add your the VMs public IP addresses to hosts.yml. Example:

```
servers:
  hosts:
    165.22.141.67:
    134.209.62.95:
    165.22.152.128:
  vars:
    ansible_python_interpreter: /usr/bin/python3
    ansible_connection: ssh
```
## Running

```
ansible-playbook playbook.yml
```

This will use ssh public key authentication automatically.

## What happens

For all the hosts specified in the hosts file, the script will
install boinc-client, configure it, and attach it to your primegrid account.
boinc-client should then do the rest. Last, it prints out the currently
running tasks on each host.


