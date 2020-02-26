# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"


Vagrant.configure('2') do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "dnsserver"
  config.vm.define "dnsserver"
  config.vm.network :private_network, ip: "192.168.53.53"
#  config.vm.forwarded_port 53, 5353, 8001
  config.vm.define :dnsserver do |dnsserver|
  end
  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.verbose = '-vv'
    ansible.limit = "powerdns_authoritative"
    ansible.playbook = "./main.yml"
    ansible.inventory_path = "./vagrant/inventory"
    ansible.become = true
  end
end
