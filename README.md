##Introduction

Easily provision 3 [ScyllaDB](https://github.com/scylladb/scylla) nodes across 3 VMs using Ansible with Vagrant & Virtualbox. 
* Ubuntu 16.04
* Latest ScyllaDB 1.7.x

##Prerequisites

* [Virtualbox](https://www.virtualbox.org/)
* [Vagrant](https://www.vagrantup.com/downloads.html)
* [Ansible](http://docs.ansible.com/intro_installation.html)

##Provisioning

Clone the project: ```git clone https://github.com/siculars/vagrant-ansible-scylla.git```

In the project directory enter: ```vagrant up```

Your cluster will be ready shortly depending on your internet connection. The initial boot takes some time as Ansible has to download, install and configure Scylla across each VM. Subsequent reboots are fast.

Scylla will be automatically configured and started once installed. Its will also be automatically started each time the VMs are booted.

Nodes will be running on: ```192.168.56.11```, ```192.168.56.12```, ```192.168.56.13```

SSH into a node with: ```vagrant ssh <nodename>```

Shutdown the VMs: ```vagrant halt```

Resume VMs: ```vagrant up```

Destroy the VMs (requires re-provisioning): ```vagrant destroy```

## Next steps

Test out your environment by:
* connecting to one of the vagrant nodes via ```vagrant ssh node<1|2|3>```, 
* then test your connection to ScyllaDB via ```cqlsh <ip address>``` by connecting to the ip address of any running nodes. Note, Ansible will apply a specific ip address to the various listener settings in ```templates/scylla.yaml```. Try ```cqlsh 192.168.56.11```.