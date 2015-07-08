# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

  config.vm.box = "cent7153vbox"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  ### Added by O.F.
  config.vm.network "private_network", type: "dhcp"

#from VBoxManage guestproperty enumerate can see second eth is as below
#  if Vagrant.has_plugin?("vagrant-hostmanager")

  config.hostmanager.ip_resolver = proc do |vm, resolving_vm|
      if vm.id
          `VBoxManage guestproperty get #{vm.id} "/VirtualBox/GuestInfo/Net/1/V4/IP"`.split()[1]
      end
      config.hostmanager.ignore_private_ip = false
      config.hostmanager.include_offline = true
      config.hostmanager.aliases = [ "vaganspup-hostm-alias" ]
  end
#  end

  config.vm.define "vaganspup-config" do |srv|
      srv.vm.hostname = "vaganspup"
      srv.vm.network "forwarded_port", guest:80, host:8081
  end
  config.vm.provision :ansible do |ansible|
      ansible.playbook = "puppetbasic.yml"
  end
end
