# Vagrant Docker

A repo for spinning up a vfagrant VM with docker for use on Mac.
Better option than boot2docker IMHO

## Plugin requirement

Requires the [Reboot Plugin](https://github.com/aidanns/vagrant-reload) for Vagrant.
This is a Vagrant 1.2+ plugin that adds the `reload` provisioning step that
will reload the VM during provisioning.

### Plugin Installation

    $ vagrant plugin install vagrant-reload
