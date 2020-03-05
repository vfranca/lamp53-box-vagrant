Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-6"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.provision "shell", inline: <<-SHELL
    yum install httpd -y
    yum install mysql-server -y
    yum install php php-mysql php-zts
    cp lamp.conf /etc/httpd/conf.d/lamp.conf
    rm /etc/httpd/conf.d/welcome.conf
    cp index.php /var/www/html/index.php
    service httpd start
    service mysqld start
    chkconfig httpd on
    chkconfig mysqld on
  SHELL
end
