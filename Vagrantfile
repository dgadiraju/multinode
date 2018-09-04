# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

require 'yaml'
cnf = YAML::load(File.open('manifest.yml'))

instances = cnf['instances']
box = cnf['box']
provider = cnf['provider']
name_prefix = cnf['name_prefix']
name_suffix = cnf['name_suffix']
ip_prefix = cnf['ip_prefix']
storage_devices = cnf['storage_devices']
disk_size = cnf['disk_size']
memory = cnf['memory']
cpus = cnf['cpus']
path = cnf['path']

Vagrant.configure("2") do |config|
  instances.times do |i|
    node_id = "#{name_prefix}#{i}"
    config.vm.define node_id do |node|
      node.vm.box = "centos/7"
      node.vm.hostname = "#{node_id}#{name_suffix}"

      node.vm.network "private_network", ip: "#{ip_prefix}#{i}"

      node.vm.provider "#{provider}" do |vm|
        vm.memory = "#{memory}"
        vm.cpus = "#{cpus}"
        if "#{provider}" === "libvirt"
          storage_devices.times do |j|
            vm.storage :file, :size => "#{disk_size}" 
          end
        end
      end
      node.vm.provision "shell", path: "#{path}"
    end
  end
end
