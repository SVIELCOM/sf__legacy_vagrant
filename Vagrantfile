# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

#box settings
  config.vm.box = "ubuntu/xenial64"

 config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
     # Customize the amount of memory on the VM:
     vb.memory = "1024"
     vb.name = "vm_for_home_b6_5"
     #set video memory size
     #vb.customize ["modifyvm", :id, "--vram", "32"]
  end

#if you need the source box update
  config.vm.box_check_update = false

#network settins
  #config.vm.network "forwarded_port", guest: 80, host: 8080
  #config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  #config.vm.network "private_network", ip: "192.168.33.10"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

    
  #Provision settings
  config.vm.provision "shell", inline: <<-SHELL
      export DEBIAN_FRONTEND=noninteractive
      export LANGUAGE=en_US.UTF-8
      export LANG=en_US.UTF-8
      export LC_ALL=en_US.UTF-8
      sudo apt-get update
      sudo apt-get install -y build-essential libreadline-dev zlib1g-dev
      wget -q https://ftp.postgresql.org/pub/source/v8.4.4/postgresql-8.4.4.tar.gz
      tar zxvf postgresql-8.4.4.tar.gz
      rm postgresql-8.4.4.tar.gz
      cd postgresql-8.4.4
      ./configure
      sudo make && make install
      sudo make clean
      export LD_LIBRARY_PATH=/usr/local/pgsql/lib
      sudo /sbin/ldconfig


#******** This section is doesn't work. It's stucks on installing postgres process :(
#locale-gen en_US.UTF-8
#sudo dpkg-reconfigure locales
#sudo ex +"%s@DPkg@//DPkg" -cwq /etc/apt/apt.conf.d/70debconf
#sudo dpkg-reconfigure debconf -f noninteractive -p critical
# Create the file repository configuration:
#sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
# Import the repository signing key:
#wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
# Update the package lists:
#sudo apt-get clean
#sudo apt-get update
#sudo dpkg --configure -a
# Install the PostgreSQL version 8.4.
#sudo apt-get -qq --ignore-hold install postgresql-8.4
#************


  SHELL
end
