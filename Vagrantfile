# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.berkshelf.enabled = true
  config.omnibus.chef_version = :latest

  config.ssh.max_tries = 40
  config.ssh.timeout   = 120

  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'
  config.vm.hostname = 'mirror-server'
  config.vm.network :private_network, ip: '33.33.33.12'

  config.vm.define :server do |server_config|
    config.vm.provision :chef_solo do |chef|
      chef.run_list = ['recipe[mirror::server]']
    end
  end

  config.vm.define :client do |client_config|
    config.vm.provision :chef_solo do |chef|
      chef.run_list = ['recipe[mirror]']
    end
  end
end
