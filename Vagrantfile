
Vagrant.configure("2") do |config|
    
    config.vm.box = "ubuntu/jammy64" 
  
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"      
      vb.cpus = 2
    end
  
    # Configuración de la red para acceder al servidor web desde el host
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Script de aprovisionamiento para instalar y configurar Apache
    config.vm.provision "shell", inline: <<-SHELL
     sudo apt-get update
     sudo apt-get install -y apache2
     sudo systemctl enable apache2
     sudo systemctl start apache2 
    SHELL
  
    config.vm.synced_folder "./html", "/var/www/html"
  end
  