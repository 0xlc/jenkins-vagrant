# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"

    config.vm.define "node01" do |node01|
        node01.vm.network "private_network", ip: "192.168.100.11"
        node01.vm.hostname = "node01.example.com"
        node01.ssh.forward_agent = true
        node01.vm.provider :virtualbox do |vb|
            vb.customize ["modifyvm", :id, "--memory", "256"]
            vb.customize ["modifyvm", :id, "--name", "node01.example.com"]
        end
        node01.vm.provision "ansible" do |ansible|
            ansible.playbook = "provisioner.yml"
        end
    end

    config.vm.define "node02" do |node02|
        node02.vm.network "private_network", ip: "192.168.100.12"
        node02.vm.hostname = "node02.example.com"
        node02.ssh.forward_agent = true
        node02.vm.provider :virtualbox do |vb|
            vb.customize ["modifyvm", :id, "--memory", "256"]
            vb.customize ["modifyvm", :id, "--name", "node02.example.com"]
        end
        node02.vm.provision "ansible" do |ansible|
            ansible.playbook = "provisioner.yml"
        end
    end
end
