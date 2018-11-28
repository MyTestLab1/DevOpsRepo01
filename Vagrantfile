# Defines our Vagrant environment
#
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|


config.vm.define "master" do |master|
     master.vm.provider "virtualbox"
     master.vm.box = "centos/7"
     master.vm.hostname = "jenkins.example.com"
     master.vm.network :private_network, ip: "10.0.0.5"
     master.vm.synced_folder ".", "/vagrant", type: "virtualbox"
     master.vm.provision "shell", inline: <<-SHELL
     sudo yum update -y
     sudo yum install git -y
     sudo yum install epel-release -y
     sudo yum install java-1.8.0-openjdk -y
     sudo wget -O /etc/yum.repos.d/jekins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
     sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
     sudo yum install jenkins -y
     sudo systemctl  start  jenkins
     sudo systemctl  status  jenkins
     SHELL
   end

end
