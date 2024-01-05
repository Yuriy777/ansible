# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "VM_A" do |vm|
      vm.vm.box = "ubuntu/bionic64"
      vm.vm.network "public_network", name: "en0", bridge: "en0: Wi-Fi"
    end
  
    config.vm.define "VM_B" do |vm|
      vm.vm.box = "ubuntu/bionic64"
      vm.vm.network "private_network", name: "en0"
    end
  
    config.vm.define "VM_C" do |vm|
      vm.vm.box = "ubuntu/bionic64"
      vm.vm.network "private_network", name: "en0"
    end
  
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_vms.yml"
      ansible.groups = {
        "VM_A" => ["VM_A"],
        "VM_B" => ["VM_B"],
        "VM_C" => ["VM_C"]
      }
    end
  end