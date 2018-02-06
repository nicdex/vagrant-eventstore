Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  # config.vm.box_check_update = false

  config.vm.network "forwarded_port", guest: 2113, host: 2113, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 1113, host: 1113, host_ip: "127.0.0.1"

  # config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get install -y curl
    curl -s https://packagecloud.io/install/repositories/EventStore/EventStore-OSS/script.deb.sh | sudo bash
    apt-get install -y eventstore-oss
    # echo 'IntIp: 192.168.33.10' >> /etc/eventstore/eventstore.conf
    # echo 'ExtIp: 192.168.33.10' >> /etc/eventstore/eventstore.conf
    service eventstore start
  SHELL
end
