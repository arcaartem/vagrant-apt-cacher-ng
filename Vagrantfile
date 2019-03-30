# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/debian-9.6"

  config.vm.hostname = "apt-cacher-ng"
  config.vm.network "private_network", ip: "10.0.100.30"

  config.vm.provision "shell", type: "shell" do |s|
    s.inline = <<-SCRIPT
      apt-get update
      apt-get install -y apt-cacher-ng
      sed -i -e '/^PassThroughPattern: /d' -e '$aPassThroughPattern: .*' /etc/apt-cacher-ng/acng.conf 
      sed -i -e '/^VerboseLog: /d' -e '$aVerboseLog: 2' /etc/apt-cacher-ng/acng.conf
      sed -i -e '/^Debug: \\.\\*/d' -e '$aDebug: 5' /etc/apt-cacher-ng/acng.conf
      systemctl restart apt-cacher-ng
      echo Acquire::http::Proxy \\"http://localhost:3142\\"\\; > /etc/apt/apt.conf.d/00aptproxy
      apt-get update
      apt-get upgrade -y
    SCRIPT
  end
end

