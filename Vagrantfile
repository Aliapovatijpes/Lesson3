# -*- mode: ruby -*-
# vi: set ft=ruby :
#Common config
Vagrant.configure("2") do |config|
 config.env.enable
 #Config for host01(MySQL server)
 config.vm.define "host01" do |host01|
  host01.vm.box = "debian/bullseye64"
  host01.vm.box_check_update = false
  host01.vm.network "public_network", ip: ENV['MYSQLIP']
  host01.vm.hostname = "host01"
  host01.vm.provision "shell", inline: <<-SHELL
   sudo apt-get update
   sudo apt-get install -y git
   git clone -b vagrant --single-branch https://#{ENV['GITLOGIN']}:#{ENV['GITTOKEN']}@github.com/Aliapovatijpes/Lesson2.git
   cd /home/vagrant/Lesson2/
    bash task2.sh -s -u #{ENV['MYSQLUSERNAME']} -p #{ENV['MYSQLUSERPASS']} -r #{ENV['ROOTPASS']} -a #{ENV['USERNAMEIP']}
  SHELL
  #This can be uncommented to local script downloading
  #host01.vm.provision "file", source: "C:/vagrant/Lesson2", destination: "$HOME/Lesson2"
  #host01.vm.provision "shell", inline: <<-SHELL 
  #  cd /home/vagrant/Lesson2/
  #  bash task2.sh -s -u #{ENV['MYSQLUSERNAME']} -p #{ENV['MYSQLUSERPASS']} -r #{ENV['ROOTPASS']} -a #{ENV['USERNAMEIP']}
  #	SHELL
   end
 #Config for host02(PHP and PHPMyAdmin server)
 config.vm.define "host02" do |host02|
  host02.vm.box = "debian/bullseye64"
  host02.vm.box_check_update = false
  host02.vm.network "public_network", ip: ENV['USERNAMEIP']
  host02.vm.hostname = "host02"
  host02.vm.provision "shell", inline: <<-SHELL
   sudo apt-get update
   sudo apt-get install -y git
   git clone -b vagrant --single-branch https://#{ENV['GITLOGIN']}:#{ENV['GITTOKEN']}@github.com/Aliapovatijpes/Lesson2.git
   cd /home/vagrant/Lesson2/
   bash task2.sh -m #{ENV['MYSQLIP']} -u #{ENV['MYSQLUSERNAME']} -p #{ENV['MYSQLUSERPASS']}
  SHELL
  #This can be uncommented to local script downloading
  #host02.vm.provision "file", source: "C:/vagrant/Lesson2", destination: "$HOME/Lesson2"
  #host02.vm.provision "shell", inline: <<-SHELL 
  #  cd /home/vagrant/Lesson2/
  #  bash task2.sh -m #{ENV['MYSQLIP']} -u #{ENV['MYSQLUSERNAME']} -p #{ENV['MYSQLUSERPASS']}
  # 	SHELL
   end
end
