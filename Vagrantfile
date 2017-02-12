Vagrant.configure(2) do |config|
    config.vm.define "webserver" do |webserver|
      webserver.vm.box = "ubuntu/xenial64"
      webserver.vm.network "private_network", ip: "192.168.0.2"
      webserver.vm.hostname = "webserver"
      webserver.vm.provision "shell", inline: <<-SHELL
          sudo apt-get update
          #Installazione necessaria per il modulo ping di ansible
          sudo apt-get -y install python-simplejson
        SHELL
      ansible.playbook = "nginx.yml"
    end
    config.vm.define "ansible" do |ansible|
      ansible.vm.box = "ubuntu/xenial64"
      ansible.vm.network "private_network", ip: "192.168.0.254"
      ansible.vm.hostname ="ansible"
      ansible.vm.provision "shell", inline: <<-SHELL
          sudo apt-get update
          #Installazione necessaria per il modulo ping di ansible
          sudo apt-get -y install python-simplejson
          #Installazione di ansible
          sudo apt-get -y install ansible
        SHELL
    end
end
