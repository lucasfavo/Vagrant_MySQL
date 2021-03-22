$script_mysql = <<-SCRIPT
  apt-get update && \
  apt-get install -y mysql-server-5.7 && \
  cat /vagrant/mysql/mysqld.cnf > /etc/mysql/mysql.conf.d/mysqld.cnf && \
  service mysql restart
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |vb|
  end

  config.vm.define "mysqlserver" do |mysqlserver|
    mysqlserver.vm.network "private_network", ip: "10.80.4.10"
    springapp.vm.network "forwarded_port", guest: 3306, host: 3306

    mysqlserver.vm.provider "virtualbox" do |vb|
      vb.name = "mysqlserver"
    end

    mysqlserver.vm.provision "shell", inline: $script_mysql
  end
end
