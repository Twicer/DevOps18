$useraddscript = <<SCRIPT
useradd -m henk
groupadd operators
usermod -aG operators henk
mkdir /operators
chown henk /operators
chgrp operators /operators
SCRIPT


Vagrant.configure('2') do |config|

    # set default settings
    config.vm.box = "ubuntu/bionic64"
    config.vm.provider "virtualbox" do |vb|
        vb.memory = 2048
        vb.cpus = 1
    end

    config.vm.define "jenkins", primary: true do |machine|
        machine.vm.host_name = "jenkins.local"
        machine.vm.network "private_network", ip: "192.168.10.189"
        config.vm.provision "shell", inline: $useraddscript

    end
end


