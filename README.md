# ansible
Ansible Deployment for Estmator


### Step 1
Collect Files
- clone ansible deployment repo
- get all the secret files
- put secret files into same directory as `deploy_django.yml`

### Step 2
Setup Ansible
- `pip install ansible` (globally)
- `pip install boto` (in virtualenv)
- `ansible-galaxy install jdauphant.nginx`

### Step 3
Use Amazon AWS Console to launch a new EC2 instance
- Instance Type: `t2.micro`
    - Specifics probably don't matter, but the process has been tested on this setup
    - Ubuntu: `ubuntu-trusty-14.04-amd64-server-20150325`
    - AMI: `ami-5189a661`
- Tags: define a tag for the instance so Ansible knows which instance(s) to target
    - key: `role`
    - value: `estmator`
- Use your normal security groups, allowing ssh, http, psql

### Step 4
Deploy!
- `ansible-playbook -i plugins/inventory/ deploy_django.yml`
- `yes` to accept fingerprint

