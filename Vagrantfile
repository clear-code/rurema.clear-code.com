# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  name = "rurema.clear-code.com"
  config.vm.define(name) do |node|
    node.vm.box = "debian-jessie-amd64"
    node.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_debian-8.2_chef-provisionerless.box"
    node.vm.network "public_network"
    node.vm.provider :virtualbox do |virtual_box|
      virtual_box.memory = 1024
    end
    node.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.groups = {
        "servers" => [name],
      }
      ansible.host_key_checking = false
    end
  end
end
