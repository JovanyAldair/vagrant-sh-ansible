# Provisioning linux machines

## Introduction

This repo. contains vagrant labs of ansible.

## Lab_01

The vagrant will execute the Vagrantfile in this directory, and will create three machine with ubuntu/lunar image:

> - Master
> - Slave01
> - Slave02

The Master is the main machine and where ansible will be installed by the scipt "provision-master.sh"

On line: 

`master.vm.provision "shell", path: "provision-master.sh"`

The Slaves will be provisioned by local ansible, where he will be install: 

* NGINX web server

On block:

`
slave01.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
end
`
And
`
slave02.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
end

## Usage

To setup this VM, execute:

`vagrant up`

To access the VM, execute:

`vagrant ssh`

To destroy the VM, execute:

`vagrant destroy -f`