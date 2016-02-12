# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    # Import the MongoDB public GPG Key and create a list file - https://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
    echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.2.list

    # Update package lists
    apt-get -y update

    # Install MongoDB
    apt-get -y install mongodb-org
  SHELL

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    # Install NVM
    curl -sS -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash
    . /home/vagrant/.bashrc
  SHELL
end
