# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
N = 3
(1..N).each do |machine_id|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.define "node#{machine_id}" do |machine|
    machine.vm.hostname = "node#{machine_id}"
    machine.vm.network "private_network", ip: "192.168.56.#{10+machine_id}"
   if machine_id == N
      machine.vm.provision :ansible do |ansible|
        ansible.limit = "all"
        ansible.playbook = "site.yml"
         config.vm.provider "virtualbox" do |v|
           v.memory = 2048
           v.cpus = 1
        end
      end
    end
  end
end
end
