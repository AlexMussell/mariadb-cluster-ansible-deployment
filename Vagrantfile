# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'


Vagrant.configure("2") do |config|

  config.vm.define "node-01" do |master|
    master.vm.hostname = "node-01"
    master.vm.box = "debian/stretch64"
    master.vm.box_check_update = false
    master.vm.network :private_network, ip: "192.168.121.235"
    config.vm.network "forwarded_port", guest: 3306, host: 3306,
      auto_correct: true
    master.vm.provider :libvirt do |v|
      v.memory = 2048
      end
  end
  
  # config.vm.define "node-02" do |slave|
  #   slave.vm.hostname = "node-02"
  #   slave.vm.box = "debian/stretch64"
  #   slave.vm.box_check_update = false
  #   slave.vm.network :private_network, ip: "192.168.121.153"
  #   config.vm.network "forwarded_port", guest: 3306, host: 3306,
  #     auto_correct: true
  #   slave.vm.provider :libvirt do |v|
  #     v.memory = 2048
  #     end
  # end

  # config.vm.define "node-03" do |slave|
  #   slave.vm.hostname = "node-03"
  #   slave.vm.box = "debian/stretch64"
  #   slave.vm.box_check_update = false
  #   slave.vm.network :private_network, ip: "192.168.121.154"
  #   config.vm.network "forwarded_port", guest: 3306, host: 3306,
  #     auto_correct: true
  #   slave.vm.provider :libvirt do |v|
  #     v.memory = 2048
  #     end
# end
end
