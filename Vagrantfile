# Defines our Vagrant environment
#
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # create mgmt node
  config.vm.define :mgmt do |mgmt_config|
      mgmt_config.vm.box = "ubuntu/trusty64"
      mgmt_config.vm.hostname = "mgmt"
      mgmt_config.vm.network :private_network, ip: "10.0.15.10"
      mgmt_config.vm.provider "virtualbox" do |vb|
        vb.memory = "256"
      end
      mgmt_config.vm.provision :shell, path: "bootstrap-mgmt.sh"
  end

  # create spring-boot
  config.vm.define :sb do |sb_config|
      sb_config.vm.box = "ubuntu/trusty64"
      sb_config.vm.hostname = "sb"
      sb_config.vm.network :private_network, ip: "10.0.15.11"
      sb_config.vm.network "forwarded_port", guest: 8080, host: 8080
      sb_config.vm.provider "virtualbox" do |vb|
        vb.memory = "768"
      end
      sb_config.vm.provision :shell, path: "bootstrap-sb.sh"
  end

end
