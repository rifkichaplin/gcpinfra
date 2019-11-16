#ENVIRONMENT INSTALLATION
virtualenv -p python3 venv
source venv/bin/activate
pip install -r requirements.txt

#CLOUDSDK just compatible with python2.7
export CLOUDSDK_PYTHON=/usr/bin/python2.7

#Setup access GCP project use gcloud
gcloud init
gcloud config list
gcloud compute instances list

#this below for ansible GCE environment
export GCE_PROJECT=$(my_project_GCP_ID)
export GCE_EMAIL=$(iam service account email)
export GCE_PEM_FILE_PATH=$(path service account file).json
export CLOUDSDK_CORE_PROJECT=$GCE_PROJECT

#create file based on environment above and run
source ~/.gce_pension-as-engineer

# gcpinfra

How to Running

ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook provision-network-bastion.yml  -vvv
ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook provision-instance-bastion.yml  -vvvv
ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook provision-instance-jenkins.yml  -vvvv
INVENTORY_TYPE=internal ANSIBLE_CONFIG="ansible-gce.cfg" ansible-playbook deploy-instance-jenkins.yml -e host_name=jenkins-machine-20180703 -vvvv

THUMBOR
------
ANSIBLE_CONFIG=ansible-gce.cfg ansible-playbook thumbor/provision_thumbor.yml
ANSIBLE_CONFIG=ansible-gce.cfg ansible-playbook thumbor/deploy_thumbor.yml  -e "host_name=thumbor-web ansible_python_interpreter=/usr/bin/python3"

PGAMESID
------
ANSIBLE_CONFIG=ansible-pgamesid.cfg ansible-playbook pgamesid_playbook/deploy_pgamesid_playbook.yml -i pgamesid_host -e "@inventories/group_vars/tag_pgamesid.yml" -e "ansible_python_interpreter=/usr/bin/python3"

MGAME
------
ANSIBLE_CONFIG=ansible-mgamecom.cfg ansible-playbook mgamedcom_playbook/deploy_mgamecom_playbook.yml -i pgamesid_host -e "@inventories/group_vars/tag_mgamecom.yml" -e "ansible_python_interpreter=/usr/bin/python3"
