# G2 Ansible IaC (Infrastructure as code) Setup docker swarm control plane (master) edition

[Ansible doc](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

## Roles
- [x] Essentials
- [x] Swap
- [x] Docker
- [x] Traefik
- [x] Reboot

## Setup
```sh
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

echo $(htpasswd -nB user) | sed -e s/\\$/\\$\\$/g
```

## Run
Add ssh config host name to `hosts`
```sh
ansible-playbook setup.yml --syntax-check
ansible-playbook setup.yml
```

## Defaults
```
Swap: 2G
Traefik: auth
```

## Test
```sh
docker node ls
docker stack ls
docker service ls

docker service update $svc --force
docker service ps --filter desired-state=running
```
