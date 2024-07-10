# basic-dns-cluster

## Installing virtual environment

PDNS Cache Lite requires python 3

```bash
python3 -m venv venv
source venv/bin/activate
pip3 install --upgrade pip
pip3 install -r requirements.txt
```

## Install required ansible roles

```
ansible-galaxy install -r requirements.yml
```

## Provisioning

Test connectivity to qa servers

```bash
ansible -m setup -i hosts all
```

Deploy and configure the PowerDNS software (single command)

```bash
# Deploy all the components in a single run
ansible-playbook  -i hosts playbook.yml --diff -v
```

Deploy and configure the PowerDNS software (split components)

```bash
ansible-playbook -i hosts playbook.yml --diff -v --tags recursor
ansible-playbook -i hosts playbook.yml --diff -v --tags dnsdist
ansible-playbook -i hosts playbook.yml --diff -v --tags auth
ansible-playbook -i hosts playbook.yml --diff -v --tags monitoring