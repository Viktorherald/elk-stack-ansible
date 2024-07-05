# -*- mode: ruby -*-end
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "box1" do |box1|
    box1.vm.box = "hashicorp/bionic64"
    box1.vm.network "private_network", ip: "192.168.56.14"
    box1.vm.hostname = "manualbox"
    
    box1.vm.synced_folder '.', '/vagrant', disabled: true
    box1.vm.synced_folder "/home/viktorng/vagrant-vms/data", "/opt/data"

    box1.vm.provider "virtualbox" do |vb|
      vb.name = "ManualBox"
      vb.memory = "2048"
      vb.cpus = "1"
    end
  end

  config.vm.define "box2" do |box2|
    box2.vm.box = "hashicorp/bionic64"
    box2.vm.network "private_network", ip: "192.168.56.15"
    box2.vm.hostname = "ansbox"
    
    box2.vm.synced_folder '.', '/vagrant', disabled: true
    box2.vm.synced_folder "/home/viktorng/vagrant-vms/data", "/opt/data"

    box2.vm.provider "virtualbox" do |vb|
      vb.name = "AnsibleBox"
      vb.memory = "8192"
      vb.cpus = "1"
    end

    box2.vm.provision "ansible" do |ansible|
      ansible.playbook = "elk-stack.yaml"
      ansible.inventory_path = "inventory"
      ansible.limit = "all"
    end
  end
end