# -*- mode: ruby -*-
# vi: set ft=ruby :
#
#Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"

require 'yaml'
servers = YAML.load_file('machine_define.yaml')

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  servers.each do |machine|
    config.vm.define machine["name"] do |srv|
      srv.vm.box = machine["box"]
      srv.vm.network machine["nettype"], ip: machine["ip"], name: machine["subnet"]
      srv.vm.provider :virtualbox do |vb|
        vb.name = machine["name"]
        vb.memory = machine["ram"]
      end
      machine["folders"].each do |dir|
        config.vm.synced_folder dir["guest"], dir["host"]
      end
      config.vm.provision :shell, :path => machine["provision_script"]
    end
  end
end
