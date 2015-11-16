# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: "192.168.33.15"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  # Shared folder from the host machine to the guest machine. Uncomment the line
  # below to enable it.
  config.vm.synced_folder ".", "/anaconda"
  config.vm.synced_folder "../anaconda_backends", "/boa"

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/vagrant.yml"
    #ansible.vault_password_file = "~/.secrets/anaconda"
  end
end
