Vagrant.configure("2") do |config|

  #System setting
  config.vm.box = "ubuntu/bionic64"

  #Provider Settings
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 4
  end

  #Network Settings
   config.vm.network "forwarded_port", guest: 3000, host: 3000

  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

   #config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.network "public_network"

  # Sync folder settings
  config.vm.synced_folder ".", "/nodeapp", { :mount_options => ["dmode=777","fmode=666"]}


 

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt install nodejs npm -y
    mkdir nodeapp
    cd /nodeapp
    sudo npm install -g nodemon
    nodemon app.js

  SHELL
end