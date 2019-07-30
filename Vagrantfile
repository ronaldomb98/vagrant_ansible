# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  #config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.network "private_network", ip: "33.33.33.33"
  config.vm.box_check_update = false
  config.vm.synced_folder "../apps/", "/var/www/", owner: "www-data", group: "www-data", :nfs => { :mount_options => ["dmode=777","fmode=777"] }
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4000"
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
    
    vb.customize ["modifyvm", :id, "--natdnsproxy2", "on"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver2", "on"]
    vb.customize ["modifyvm", :id, "--nictype2", "virtio"]

    vb.customize ["modifyvm", :id, "--natdnsproxy3", "on"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver3", "on"]
    vb.customize ["modifyvm", :id, "--nictype3", "virtio"]
    
    vb.customize ["modifyvm", :id, "--natdnsproxy4", "on"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver4", "on"]
    vb.customize ["modifyvm", :id, "--nictype4", "virtio"]
  end
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"

  end
end
