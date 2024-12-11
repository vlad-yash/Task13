# -*- mode: ruby -*-
# vi: set ft=ruby :

$install_deps = <<-'SHELL'
# TODO: your code here
apt-get update -y
apt-get install -y openjdk-17-jdk
SHELL

Vagrant.configure("2") do |config|
  # TODO: your code here
  config.vm.box = "ubuntu/jammy64"
  config.vm.box_version = "20241002.0.0"
  config.vm.network "private_network", ip: "192.168.100.100"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = "4"
  end
  config.vm.provision "shell", inline: $install_deps
  config.trigger.after :up do |trigger|
    trigger.run_remote = {inline: "cd /vagrant && sed -i -e 's/\r$//' ./gradlew && ./gradlew bootRun"} 
  end
end