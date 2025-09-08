# Ansible Automation: Webserver Deployment on AWS EC2

## Demo of the project

[Watch the demo on SJSU OneDrive](https://sjsu0-my.sharepoint.com/:v:/g/personal/akshata_madavi_sjsu_edu/EZ5Zlv4B3NBNsV9fPQNuXF4BiPQxkiuwrSwkLww-Lpgcpw?e=ayyenf)

<video src="https://raw.githubusercontent.com/Akshata4/enterprise_software_platform/refs/heads/main/ansible-playbook/video/video1816555058.mp4" width="640" height="360" controls></video>

<video width="640" height="360" controls>
  <source src="https://raw.githubusercontent.com/Akshata4/enterprise_software_platform/refs/heads/main/ansible-playbook/video/video1816555058.mp4" type="video/mp4">
</video>



## Project Overview
This project automates the deployment of Nginx webservers on two AWS Ubuntu EC2 instances (`esp-v1` and `esp-v2`) running in the `us-east-2` region. Each webserver listens on port 8080 and serves a custom web page showing the message:

**"Hello World from SJSU-X"**, where **X** is the VM number (1 or 2).

## Prerequisites
- AWS EC2 Ubuntu instances running and accessible.
- Ansible installed on control machine.
- SSH key with access to EC2 instances.

## Inventory (`inventory.ini`)
`[aws]`
`esp-v1 ansible_host=<IP_of_esp-v1> ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/key.pem`
`esp-v2 ansible_host=<IP_of_esp-v2> ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/key.pem`


## Usage

### Deploy the webservers:
`ansible-playbook -i inventory.ini deploy_webserver.yaml `



## Playbook Details
- `deploy_webserver.yaml` contains two plays: one to deploy and configure Nginx, and one to undeploy (stop and remove) Nginx.
- Uses Jinja2 templates in the `templates` directory for Nginx config (`nginx_custom.conf.j2`) and web page (`index.html.j2`).

## Directory Structure
```bash
ansible-playbook/
│
├── deploy_webserver.yaml
├── inventory.ini
├── templates/
│   ├── nginx_custom.conf.j2
│   └── index.html.j2
└── test/
```

