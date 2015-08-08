# -*- mode: ruby -*-
# vi: set ft=ruby :

$dockerinit = <<SCRIPT
echo Install Docker
apt-get update
apt-get install wget
wget -qO- https://get.docker.com/ | sh
#vagrant user can use docker
usermod -aG docker vagrant
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.provision "shell", inline: $dockerinit
end
