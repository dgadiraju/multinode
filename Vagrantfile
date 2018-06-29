# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
require 'yaml'
cnf = YAML::load(File.open('manifest.yml'))
instances = cnf['instances'].to_i

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  instances.times do |i|
    node_id = cnf['name_prefix'] + "#{i}"
    config.vm.define node_id do |node|
      node.vm.box = "centos/7"
      node.vm.hostname = "#{node_id}"
      node.vm.network "private_network", ip: cnf['privateip_prefix'] + "#{i}"
      node.vm.provider :libvirt do |lvm|
        lvm.memory = cnf['memory']
        lvm.cpus = cnf['cpus']
        lvm.storage :file, :size => '60G'
        lvm.storage :file, :size => '60G'
      end
      node.vm.provision "shell", path: cnf["bootstrap"]
    end
  end
end

