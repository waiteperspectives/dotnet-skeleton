# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :dotnet do |dotnet|
    dotnet.vm.box = "ubuntu/focal64"
    dotnet.disksize.size = "10GB"
    dotnet.vm.hostname = "dotnet"
    dotnet.vm.network :private_network, ip: "192.168.50.50"
    dotnet.vm.synced_folder "src/", "/home/vagrant/src"
    dotnet.vm.network "forwarded_port", guest: 2113, host: 2113

    dotnet.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.cpus = "2"
      vb.name = "dotnet"
    end

    dotnet.vm.provision :shell, :inline => "sudo rm /etc/localtime && sudo ln -s /usr/share/zoneinfo/America/New_York /etc/localtime", run: "always"

    dotnet.vm.provision "ansible" do |ansible|
      ansible.playbook = "./provisioning/playbooks/setup_node.yaml"
    end

    dotnet.vm.provision "ansible" do |ansible|
      ansible.playbook = "./provisioning/playbooks/setup_vim.yaml"
    end

    dotnet.vm.provision "ansible" do |ansible|
      ansible.playbook = "./provisioning/playbooks/setup_dotnet.yaml"
    end

    dotnet.vm.provision "ansible" do |ansible|
      ansible.playbook = "./provisioning/playbooks/setup_eventstore.yaml"
    end

  end
end
