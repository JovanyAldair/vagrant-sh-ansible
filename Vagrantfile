# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

 
  config.vm.define "master" do |master|
    master.vm.box = "ubuntu/lunar64"
    master.vm.hostname = "Master"
    master.vm.network "private_network", ip: "192.168.57.14"

    master.vm.provision "shell", path: "provision-master.sh"
    
    master.vm.provider "virtualbox" do |vb|
      vb.name = "Master"
      vb.memory = "256"
      vb.cpus = 1
    end
  end

  config.vm.define "slave01" do |slave01|
    slave01.vm.box = "ubuntu/lunar64"
    slave01.vm.hostname = "Slave01"
    slave01.vm.network "private_network", ip: "192.168.57.15"

    slave01.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
    end

    slave01.vm.provider "virtualbox" do |vb|
      vb.name = "Slave01"
      vb.memory = "256"
      vb.cpus = 1
    end
  end
  
  config.vm.define "slave02" do |slave02|
    slave02.vm.box = "ubuntu/lunar64"
    slave02.vm.hostname = "slave02"
    slave02.vm.network "private_network", ip: "192.168.57.16"
    
    slave02.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
    end

    slave02.vm.provider "virtualbox" do |vb|
      vb.name = "slave02"
      vb.memory = "256"
      vb.cpus = 1
    end
  end
end
