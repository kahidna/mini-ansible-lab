# MINI ANSIBLE LAB

Ansible is a radically simple IT automation engine that automates cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT needs. This tool very helping devops to manage server or any instance which support ssh service. To understand about ansible, will be more fun if we can do trial and test ansible on the real instance. But since creating virtual machine or init a vps could be need more resource and spend some money, 

I came up with idea how if we use container as instance? Because container have some feature/capability like real instance/vm/vps.  Take an example like install service, start or stop the service, config the service, and also accessing the port. With this feature, we can research or developing playbook for ansible which have needs as mentioned.But of course container also have limitation like cannot manage iptables, or any stuff related with kernel, so learning ansible using container would also have the same restrictions. So make sure you understand the requirement you need before use this repository.

# Project structure & information
For more convenient when we want to re-use the repository, I use docker volume for persist the configuration or any data which need to be persist such as pair key and ansible configuration. Ansible doesn't need custom or certain agent since its use ssh as media for communation to each instance. So here is the project structure :

<pre>
mini-ansible-lab
 ├── docker-compose.yml           - you can add more node by copying and pasting the service, don't forget to change the hostname,ip address and container name
 ├── images
 │   ├── client-image
 │   │   └── Dockerfile           - Dockerfile for Base Image for client node
 │   └── master-image
 │       └── Dockerfile           - Dockerfile for Base Image for master node
 ├── master-ansible
 │   ├── ansible.cfg              - ansible configuration fornmater node
 │   └── hosts                    - inventory hosts, or you can say this is list of hosts client which can controlled using ansible
 ├── master-node-volume           - additional folder to store your personal data when you try to push or pull files/folders using ansible
 ├── README.md                    - documentation for this repository
 ├── ssh-node-client
 │   └── authorized_keys          - public key file which shared to client, copied from mini-ansible-lab.pub
 └── ssh-node-master
     ├── mini-ansible-lab.pem     - private key of the pair key
     └── mini-ansible-lab.pub     - public key of the pair key

</pre>

This repository use <a href="https://github.com/rastasheep/ubuntu-sshd">rastasheep ubuntu-sshd</a> as base image (which using ubuntu as base os) for the each container. You can check the image on docker hub repository on <a href="https://github.com/rastasheep/ubuntu-sshd">here</a>. And if you want to change the base image you need to modify **docker-compose.yml** on image section, and also change the base os/image n **Dockerfile**.


# Environment
Here is the environment when I create the repository and deploy it on my local machine :   
- ubuntu 18.04.1 LTS
- docker-compose 1.22.0
- docker 18.03.1-ce

Some configuration already changed by me to make sure this repo ready to use, here is the configuration
changed on ansible.cfg :
```
host_key_checking = False
private_key_file = /root/.ssh/mini-ansible-lab.pem
inventory      = /etc/ansible/hosts
```

# Issue and suggestion
Please feel free to create issue if you have suggestion or problem with this repository. :)

# License

MIT

Copyright (c) 2018 Alfin Hidayat
