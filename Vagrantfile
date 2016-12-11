# -*- mode: ruby -*-
# # vi: set ft=ruby :
 
# Specify minimum Vagrant version and Vagrant API version
Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"
 
# Require YAML module
require 'yaml'
 
# Read YAML file with box details
machines = YAML.load_file(File.join(File.dirname(__FILE__), 'machine_define.yaml'))
 
# Create boxes
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

  # Iterate through entries in YAML file
  machines.each do |servers|
    config.vm.define servers["name"] do |srv|
      srv.vm.box = servers["box"]
      srv.vm.box_check_update = true
      srv.vm.box_url = servers["boxurl"]
      srv.vm.hostname = servers["name"]
      srv.vm.network "private_network", ip: servers["ip"], name: servers["subnet"]
      srv.vm.provider :virtualbox do |vb|
        vb.name = servers["vm_name"]
        vb.memory = servers["ram"]
      end
      srv.vm.provision "ansible" do |a|
        a.limit = servers["name"]
        a.verbose = "v"
        a.playbook = "playbooks/ntp.yml"
      end
    end
  end
end
