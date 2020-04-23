# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  (1..2).each do |i|

    if i == 1 then
      vm_name = "master-node"
    else
      vm_name = "worker-node"
    end

    config.vm.define vm_name do |s|
      s.vm.hostname = vm_name
      s.vm.box = "centos/7"
      s.vm.box_check_update = false
      private_ip = "172.16.20.#{i+9}"
      s.vm.network "private_network", ip: private_ip
    
      s.vm.provider "virtualbox" do |vb|
        vb.gui = false
        if i == 1 then
          vb.cpus = 2
          vb.memory = "2048"
        else
          vb.cpus = 2
          vb.memory = "1024"
        end
      end
      
      s.vm.provision :shell, "privileged": true, path: "./init.sh"
    end
  end
end
