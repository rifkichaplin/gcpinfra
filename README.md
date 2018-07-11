# gcpinfra

How to Running

ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook provision-network-bastion.yml  -vvv
ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook provision-instance-bastion.yml  -vvvv
ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook provision-instance-jenkins.yml  -vvvv
INVENTORY_TYPE=internal ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook deploy-instance-jenkins.yml -e host_name=jenkins-machine-20180703 -vvvv
