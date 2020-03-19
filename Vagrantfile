# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'


Vagrant.configure("2") do |config|

  config.vm.define "node-01" do |master|
    master.vm.hostname = "node-01"
    master.vm.box = "debian/stretch64"
    master.vm.box_check_update = false
    master.vm.network :private_network, ip: "192.168.121.235"
    master.vm.provider :libvirt do |v|
      v.memory = 2048
      end
  end
  
  config.vm.define "node-02" do |slave|
    slave.vm.hostname = "node-02"
    slave.vm.box = "debian/stretch64"
    slave.vm.box_check_update = false
    slave.vm.network :private_network, ip: "192.168.121.153"
    slave.vm.provider :libvirt do |v|
      v.memory = 2048
      end
  end

  config.vm.define "node-03" do |slave|
    slave.vm.hostname = "node-03"
    slave.vm.box = "debian/stretch64"
    slave.vm.box_check_update = false
    slave.vm.network :private_network, ip: "192.168.121.154"
    slave.vm.provider :libvirt do |v|
      v.memory = 2048
      end
  end
end
