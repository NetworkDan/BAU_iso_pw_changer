# -*- mode: ruby -*-
# vi: set ft=ruby :
$containter_provision =

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.define "lastpass_cli" do |lastpass_cli|
    runner.vm.provider "virtualbox" do |vb|
      vb.cpus = 1
      vb.memory = 1024
      vb.linked_clone = true
    end
    lastpass_cli.vm.hostname = "lastpass_cli"
    lastpass_cli.vm.network "private_network", ip: "172.20.20.90"
    lastpass_cli.vm.provision "docker"
    lastpass_cli.vm.provision "shell", inline: "docker pull morfien101/terraform-runner"
    lastpass_cli.vm.provision "shell", inline: $containter_provision
  end
end
