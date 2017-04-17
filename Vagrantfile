# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "forman" do |foreman|
    foreman.vm.box = "centos/7"
    foreman.vm.hostname = "foreman"
    foreman.vm.network "private_network", ip: "192.168.255.254", virtualbox__intnet: "pxe_network"
    foreman.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/foreman.yml"
      ansible.sudo = true
      ansible.extra_vars = {
        isc_dhcp_server_subnet: [
          {
            netaddress: "192.168.255.0",
            netmask: "255.255.255.0",
            gateway: "192.168.255.254",
            domain: "lab.local",
            domain_search: "lab.local",
            dns: "192.168.255.254",
            range: "192.168.255.20 192.168.255.100"
          }
        ]
      }
    end
  end

  # config.vm.define "dhcl01" do |dhcl01|
  #   dhcl01.vm.box = "precise64"
  #   dhcl01.vm.box_url = "http://files.vagrantup.com/precise64.box"
  #   dhcl01.vm.provider :virtualbox do |box|
  #     box.customize ["modifyvm", :id, "--name", "dhcl01" ]
  #     box.customize ["modifyvm", :id, "--nic2", "intnet" ]
  #   end

end
