# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "4096"
    vb.cpus = 2
  end

  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"
  config.vm.provision "shell", inline: <<-SHELL
    cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
  SHELL
  
  config.vm.define "centos7_webmin" do |config|
    config.vm.box = 'centos/7'
    config.vm.hostname = 'webmin.loc'
    config.vm.provision "shell", path: "bootstrap.sh"

    # webmin port
    config.vm.network "forwarded_port", id: "centos7_webmin", guest: 10000, host: 10000, guest_ip: "10.0.2.15", host_ip: "127.0.0.1", protocol: "tcp"
    # http port
    config.vm.network "forwarded_port", id: "centos7_http", guest: 80, host: 8080, guest_ip: "10.0.2.15", host_ip: "127.0.0.1", protocol: "tcp"
    # https port
    config.vm.network "forwarded_port", id: "centos7_https", guest: 443, host: 4430, guest_ip: "10.0.2.15", host_ip: "127.0.0.1", protocol: "tcp"
  end

end
