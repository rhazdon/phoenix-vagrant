# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.synced_folder ".", "/vagrant"
  config.vm.define "dev", primary: true do |dev|
    config.vm.network "private_network", ip: "10.10.10.10"
    config.vm.network :forwarded_port, guest: 4000, host: 4000
    config.vm.provision "ansible" do |ansible|
      ansible.host_key_checking = false
      ansible.playbook = "provisioning/playbook.yml"
      ansible.inventory_path = "provisioning/development"
      ansible.limit = "all"
    end
  end
end
