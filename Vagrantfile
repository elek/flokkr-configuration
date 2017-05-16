
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.provision "docker"

  config.vm.provider "virtualbox" do |v|
     v.customize ["modifyvm", :id, "--memory", 3000]
     v.customize ["modifyvm", :id, "--cpus", 4]
  end

  config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.provision :docker_compose, yml: "/vagrant/vagrant/node1.yaml", run: "always"
    node1.vm.network "private_network", ip: "192.168.50.4"
    node1.vm.provision :hosts, :sync_hosts => true
  end

  config.vm.define "node2" do |node2|
    node2.vm.hostname = "node2"
    node2.vm.provision :docker_compose, yml: "/vagrant/vagrant/node2.yaml", run: "always"
    node2.vm.network "private_network", ip: "192.168.50.5"
    node2.vm.provision :hosts, :sync_hosts => true
  end


end
