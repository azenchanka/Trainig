$install = <<-SCRIPT
yum -y install git
SCRIPT
$hosts = <<-SCRIPT
echo "192.168.56.101	server1 server1" >> /etc/hosts
echo "192.168.56.102	server2 server2" >> /etc/hosts
SCRIPT
$git_clone = <<-SCRIPT
git clone https://github.com/azenchanka/Trainig.git
SCRIPT
$list = <<-SCRIPT
cd /home/vagrant/Trainig
cat task2
SCRIPT

Vagrant.configure("2") do |config| 
  config.vm.box = "bertvv/centos72"
  config.vm.provision "shell", inline: $hosts

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end

  config.vm.define "server1" do |server1|
    server1.vm.provision "shell", inline: $install
    server1.vm.provision "shell", inline: $git_clone
    server1.vm.provision "shell", inline: $list
    server1.vm.hostname = "server1"
    server1.vm.network "private_network", ip: "192.168.56.101"
  end

  config.vm.define "server2" do |server2|
    server2.vm.hostname = "server2"
    server2.vm.network "private_network", ip: "192.168.56.102"
  end

end
