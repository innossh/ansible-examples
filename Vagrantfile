# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.box = "centos64-x86_64-20140116"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.4.2/centos64-x86_64-20140116.box"

  local_vms = ""
  if File.exists?("vars/common.yml")
    require "yaml"
    configuration = YAML.load_file("vars/common.yml")
    local_vms = configuration["local_vms"] if configuration["local_vms"]
  end

  config.vm.define :gitbucket do |gitbucket|
    gitbucket.vm.hostname = "vm-gitbucket"
    gitbucket.vm.network "private_network", ip: "192.168.33.11"
    gitbucket.hostsupdater.aliases = [local_vms["gitbucket"]["hosts"]]

    gitbucket.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end

    gitbucket.vm.provision :ansible do |ansible|
      ansible.playbook = "GitBucket/site.yml"
      ansible.inventory_path = "GitBucket/inventories/local"
    end
  end

end
