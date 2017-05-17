
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.provision "docker"

  config.vm.provider "virtualbox" do |v|
     v.customize ["modifyvm", :id, "--memory", 3000]
     v.customize ["modifyvm", :id, "--cpus", 4]
  end

  config.vm.define "node1" do |node|
    node.vm.hostname = "node1"
    node.vm.provision :docker_compose, yml: "/vagrant/vagrant/node1.yaml", run: "always"
    node.vm.network "private_network", ip: "192.168.50.11"
    node.vm.provision :hosts, :sync_hosts => true
  end

  config.vm.define "node2" do |node|
    node.vm.hostname = "node2"
    node.vm.provision :docker_compose, yml: "/vagrant/vagrant/node2.yaml", run: "always"
    node.vm.network "private_network", ip: "192.168.50.12"
    node.vm.provision :hosts, :sync_hosts => true
  end

  config.vm.define "node3" do |node|
    node.vm.hostname = "node3"
    node.vm.provision :docker_compose, yml: "/vagrant/vagrant/node3.yaml", run: "always"
    node.vm.network "private_network", ip: "192.168.50.13"
    node.vm.provision :hosts, :sync_hosts => true
  end

end
