# training-ansible
Ansible basics

## Requirements
* VirtualBox
* Vagrant
* Vagrant's plugin _vagrant-vbguest_

## HowTo
```
vagrant up
vagrant ssh bastion
cd ansible
ansible -m ping all
```
