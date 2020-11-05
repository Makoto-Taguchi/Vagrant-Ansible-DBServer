# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"

  config.vm.network "private_network", ip: "192.168.56.46"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "512"
  end
   
  config.vm.provision "ansible" do |ansible|
    # ansible.playbook = "ansible/playbook.yml"
    ansible.playbook = "ansible/tasks/main.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.limit = 'all'
  end
end

