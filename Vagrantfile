# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.disksize.size = "10GB"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = "2"
    vb.name = "tmp-dotnet"
  end
  config.vm.provision :shell, :inline => "sudo rm /etc/localtime && sudo ln -s /usr/share/zoneinfo/America/New_York /etc/localtime", run: "always"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./provisioning/playbooks/setup_node.yaml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./provisioning/playbooks/setup_vim.yaml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./provisioning/playbooks/setup_dotnet.yaml"
  end
end
