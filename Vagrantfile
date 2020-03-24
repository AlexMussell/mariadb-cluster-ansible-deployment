# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

CLUSTER_SIZE = 3

Vagrant.configure("2") do |config|

  (1..CLUSTER_SIZE).each do |id|
    config.vm.define "node-#{id}" do |node|
      node.vm.hostname = "node-#{id}"
      node.vm.box = "debian/stretch64"
      node.vm.box_check_update = false
      node.vm.network :private_network, ip: "192.168.121.#{20+id}"
      config.vm.network "forwarded_port", guest: 3306, host: 3306,
        auto_correct: true
      node.vm.provider :libvirt do |v|
        v.memory = 2048
      end
    
      if id == CLUSTER_SIZE
        node.vm.provision :ansible do |ansible|
          ansible.limit = "all"
          ansible.become = true
          ansible.playbook = "playbooks/mariadb_cluster.yml"
          ansible.groups = {
            "mariadb_cluster" => ["node-1", "node-2", "node-3"]
          }
        end
      end
    end
  end
end