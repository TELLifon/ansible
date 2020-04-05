# Ansible Helpers for setting up TELLifon Infra

## Infra Overview

All systems run on Ubuntu 18.04.

### Rancher Node aka Gessler

We run one Rancher Node quick and easy - Install Docker and start the Rancher container.

`sudo docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher`

After creating the Cluster within Rancher we can install an join the Kubernetes nodes

### Kubernetes Nodes

All Kubernetes Nodes are bootstrapped via the `rancher.yml` playbook.
Make sure you update the Rancher command so it connects to the correct Rancher Node.

`ansible-playbook playbooks/rancher.yml -i hosts -b`

## Create Admin Users

The `users.yml` playbook makes sure all admin users have access to the system:

`ansible-playbook playbooks/users.yml -i hosts -b`
