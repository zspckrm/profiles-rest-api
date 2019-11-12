# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
 # The most common configuration options are documented and commented below.
 # For a complete reference, please see the online documentation at
 # https://docs.vagrantup.com.

 # Every Vagrant development environment requires a box. You can search for
 # boxes at https://vagrantcloud.com/search.
 config.vm.box = "ubuntu/bionic64"
 config.vm.box_version = "~> 20190314.0.0"

# host is the desktop
# guest is the virtual server
 config.vm.network "forwarded_port", guest: 8000, host: 8000

# Script to run when the server is created
 config.vm.provision "shell", inline: <<-SHELL
   systemctl disable apt-daily.service    # disable auto update
   systemctl disable apt-daily.timer      # disable auto update

   sudo apt-get update  # update loccal repository with all available pacckages
   sudo apt-get install -y python3-venv zip  # install python3
   touch /home/vagrant/.bash_aliases
   if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
     echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
     echo "alias python='python3'" >> /home/vagrant/.bash_aliases
   fi
 SHELL
end
