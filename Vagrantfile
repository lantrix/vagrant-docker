# -*- mode: ruby -*-
# vi: set ft=ruby :

$dockerinit = <<SCRIPT
echo Install Docker
curl https://get.docker.com/ | sh
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.provision "shell", inline: $dockerinit
end
