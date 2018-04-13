#!/usr/bin/env ruby
# Creates an Ubuntu 14.04 VM
#   * Run using 'vagrant up'
#   * SSH using vagrant@192.168.10.10, password 'vagrant'

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "192.168.10.10"
  config.vm.network "forwarded_port", guest: 8443, host: 8080

    config.vm.provider "virtualbox" do |vb|
   	 vb.memory = "6144"
   	 vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end
end
