# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.provider :virtualbox do |vb, override|
    override.vm.box = "precise32js"
    override.vm.box_url = "http://files.vagrantup.com/precise32.box"

    vb.customize ['modifyvm', :id, "--memory", "1024"]
  end

  # Forwards the following ports between the Host and Guest machine
  # If there is a collision on the host, it will automatically re-assign the host port
  config.vm.network :forwarded_port, guest: 8001, host: 8001, auto_correct: true
  config.vm.network :forwarded_port, guest: 8002, host: 8002, auto_correct: true

  # Share the projects folder if it exists on the Host Machine
  if File.exists?("projects")
    config.vm.synced_folder "projects", "/home/vagrant/projects"
  end
  config.vm.provision :shell, :path => "provision.sh"

end

