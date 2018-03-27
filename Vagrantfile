# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = 'bento/centos-7.3'
  config.ssh.forward_agent = true

  config.vm.define 'server' do |host|
    host.vm.hostname = 'server'
    host.vm.network 'private_network', ip: '192.168.33.10'
    host.vm.provision :ansible do |ansible|
      ansible.playbook       = 'sample.yml'
      ansible.groups = {
        'vagrant' => ['server']
      }
#      ansible.tags           = ['init']
#      ansible.verbose        = true
#      ansible.raw_arguments = '-vvvv'
      ansible.raw_ssh_args   = ['-o ForwardAgent=yes']
    end
  end
end
