# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Ansible
  provision_config = {
    :playbook => "site.yml",
    :inventory_path => "inventory/hosts",
    :verbose => "v"
  }

  # Master DB
  config.vm.define "mysql-master" do |vm01|
    vm01.vm.hostname = "an-db01-master"
    vm01.vm.box = "centos/7"
    vm01.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    vm01.vm.network "private_network", ip: "192.168.56.46"
    vm01.vm.network :forwarded_port, id: "ssh", host: 2224, guest: 22
    vm01.vm.provision :ansible, provision_config.merge(:limit => "mysql-master")
  end

  #  Slave DB
  config.vm.define "mysql-slave" do |vm02|
    vm02.vm.hostname = "an-db02-slave"
    vm02.vm.box = "centos/7"
    vm02.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    vm02.vm.network "private_network", ip: "192.168.56.47"
    vm02.vm.network :forwarded_port, id: "ssh", host: 2225, guest: 22
    vm02.vm.provision :ansible, provision_config.merge(:limit => "mysql-slave")
  end

  # config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  # Ansible
  # config.vm.provision "ansible" do |ansible|
  #   ansible.playbook = "ansible/tasks/main.yml"
  #   ansible.inventory_path = "ansible/hosts"
  #   ansible.limit = 'all'
  # end

end

