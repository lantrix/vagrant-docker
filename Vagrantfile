# -*- mode: ruby -*-
# vi: set ft=ruby :

$predocker = <<SCRIPT
echo Pre Docker requirements
sed -i 's/^mesg n$/tty -s \&\& mesg n/g' /root/.profile
apt-get update
apt-get install wget
apt-get install -y linux-image-virtual linux-image-extra-virtual
SCRIPT

$dockerinit = <<SCRIPT
echo Install Docker
wget -qO- https://get.docker.com/ | sh
#vagrant user can use docker
usermod -aG docker vagrant
SCRIPT

#Requires Vagrant Reload plugin
#https://github.com/aidanns/vagrant-reload
Vagrant.configure(2) do |config|
  config.vm.box = "hashicorp/precise64"

  #Needed to be disabled for HGFS problems
  config.vm.synced_folder ".", "/vagrant", disabled: true

  #Fix tty errors
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
  config.vm.provision :shell,
    :inline => "sed -i 's/^mesg n$/tty -s \\&\\& mesg n/g' /root/.profile"

  #Pre-reboot provision
  config.vm.provision "shell", inline: $predocker

  # Run a reboot of a *NIX guest.
  config.vm.provision :reload

  #Post-reboot provision
  config.vm.provision "shell", inline: $dockerinit

end
