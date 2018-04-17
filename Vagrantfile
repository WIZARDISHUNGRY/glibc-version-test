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

  # target
  # config.vm.define "ubuntu-old" do |web|
  #   config.vm.box = "ubuntu/xenial64"
  #   config.vm.hostname = "rack-ubuntu-old"
  # end

  # works
  # config.vm.define "debian-stretch" do |web|
  #   config.vm.box = "generic/debian9"
  #   config.vm.hostname = "rack-debian-stretch"
  # end

  # config.vm.define "debian-buster" do |web|
    config.vm.box = "fujimakishouten/debian-buster64"
    config.vm.hostname = "rack-debian-buster"
  # end

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true

    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  config.ssh.extra_args = %W(-o AddKeysToAgent=yes)

  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
 config.vm.provision "shell", inline: <<-SHELL
   sudo add-apt-repository -y ppa:ubuntu-toolchain-r/test
   sudo apt-get update
   sudo apt-get upgrade -y
   sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y &&
    sudo apt-get update && sudo apt-get install gcc-snapshot -y &&
    sudo apt-get update && sudo apt-get install gcc-7 g++-7 -y
   sudo apt-get install -y git libx11-dev \
    libxrandr-dev libxinerama-dev libxcursor-dev libgl1-mesa-dev \
    libglu1-mesa-dev zlib1g-dev libasound2-dev libgtk2.0-dev unzip zip cmake \
    libudev-dev libusb-dev bison flex protobuf-compiler libspeexdsp1 libprotobuf-c-dev \
    libprotobuf-dev \
    xorg openbox \
    ;
    curl https://vcvrack.com/downloads/Rack-0.6.0-lin.zip -o ~vagrant/Rack-0.6.0-lin.zip
 SHELL
end
