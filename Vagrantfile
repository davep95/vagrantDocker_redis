# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "dp-docker"
  config.vm.provision "docker" do |d|
    d.build_image "/vagrant/nginx/"
    d.build_image "/vagrant/redis/"
  end
end
