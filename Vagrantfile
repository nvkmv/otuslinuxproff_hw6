# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "nvkmv/rockylinux9"
  config.vm.box_version = "2.0"
  
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "ansible/playbook.yml"
  end  

  config.vm.provider "virtualboxi" do |v|
    v.memory = 256
    v.cpus = 1
  end

  config.vm.define "server" do |server|
    server.vm.hostname = "server"
    server.vm.network "private_network", ip: "192.168.56.66", virtualbox__inet: "net1"
  end

  config.vm.define "client" do |client|
    client.vm.hostname = "client"
    client.vm.network "private_network", ip: "192.168.56.67", virtualbox__inet: "net1"
  end
end
