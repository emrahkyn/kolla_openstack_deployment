# kolla openstack multi-node deployment
This is a repository which covers all required steps for a standalone operating system (Ubuntu 20.04) to deploy core openstack services using kolla-ansible multi-node deployment

It has 3 main parts such as 1-post_foreman_set_static_ip,  2-pre_installation and 3-kolla-ansible-deployment. 

- First, it basically edits the netplan config file based on inventory hostname and changes the interface ip address. 
- Second, it creates a number of users, updates & upgrades packages, sets timezone & ntp server, configures physical network and bridges for preparation of openstack deployment. 
- Third, openstack self-service network deployment using multi-node kolla-ansible. Kolla-ansible is installed via python virtual environment, and ansible 2.10.15  version is used.

All neccessary files for openstack deployment are available under 3-kolla-ansible-deployment/config folder. Users do not have to do additional tasks to reach an openstack platform deployment. At the end, the platform should be ready for provisioning after following commands are executed successfully.

- kolla-ansible --configdir config -i inventory.ini bootstrap-servers
- kolla-ansible --configdir config -i inventory.ini prechecks
- kolla-ansible --configdir config -i inventory.ini deploy
