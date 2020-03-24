# MariaDB Cluster Deployment with Ansible (inc. Vagrant Test Environment)
A MariaDB 10.4 Galera cluster deployment, and a Vagrant (KVM) test deployment. Currently only for Debian, but will be for other OS's in the near future. If you require help installing KVM and Vagrant, I have done a guide [here](https://alexandermussell.com/kvm/vagrant/ubuntu18.04/virtualisation/2020/03/17/kvm-vagrant-environment.html).

## WIP
__TODO__: Deploy for Redhat, Fedora, Docker, Convert all options to vars, Create a small app that uses the service (deployed by vagrant), perform backups to a backup node, create an arbitrator.

__COMPLETE__: Basic Debian deployment (tested on Debian 9 (Stretch))

## Vagrant
To deploy a vagrant test cluster, just run `vagrant up`. Once the nodes are creates, to update MariaDB configurations, run `vagrant provision`. The reason I kept a vagrant inventory is to provide an example inventory file for further deployments.

## Development, Staging, and Production Environments
Once you have tested via Vagrant, and have some VM's ready in whatever cloud solution you have, provide a new inventory file (I usually name them by environment, eg. `vagrant`, `dev`, `stage`, `prod`) following the same structure as the example file, then add your vm IPs to the `ansible_host` variable and deploy with `ansible-playbook -p playbooks/mariadb_cluster.yml -i <env>`.

Please create PRs if you fancy collaborating. This is free to use by anybody.
