# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<END
RUBY_VERSION="2.2.5"
sudo apt-get -y update
sudo apt-get -y install git nodejs
# Install ruby environment
if ! type rvm >/dev/null 2>&1; then
  curl -sSL https://rvm.io/mpapis.asc | gpg --import -
  curl -sSL https://get.rvm.io | bash -s stable
  source /etc/profile.d/rvm.sh
fi

if ! rvm list rubies ruby | grep ruby-${RUBY_VERSION}; then
  rvm install ${RUBY_VERSION}
fi

rvm --default use ${RUBY_VERSION}
rvm all do gem install middleman
END

Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.ssh.forward_agent = true

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.hostname = "vagrant"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]

    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision "shell", inline: $script
end
