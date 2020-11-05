# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  # Master DB
  config.vm.define "node1" do |vm01|
    vm01.vm.hostname = "an-db01-master"
    vm01.vm.box = "centos/7"
    vm01.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    vm01.vm.network "private_network", ip: "192.168.56.46"
    vm01.vm.network :forwarded_port, id: "ssh", host: 2224, guest: 22
  end

  #  Slave DB
  config.vm.define "node2" do |vm02|
    vm02.vm.hostname = "an-db02-slave"
    vm02.vm.box = "centos/7"
    vm02.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    vm02.vm.network "private_network", ip: "192.168.56.47"
    vm02.vm.network :forwarded_port, id: "ssh", host: 2225, guest: 22
  end

  # Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/tasks/main.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.limit = 'all'
  end

end

