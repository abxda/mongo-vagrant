Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"

  # Configuración de la red: reenvío de puerto
  config.vm.network "forwarded_port", guest: 27017, host: 27017

  config.vm.provision "shell", inline: <<-SHELL
    sudo touch /etc/mongod.conf
    echo "bindIp: 127.0.0.1" >> /etc/mongod.conf
    # Instalación de MongoDB y ajustes de configuración
    sudo apt-get update
    sudo apt-get install -y mongodb
    sudo systemctl restart mongodb
  SHELL
end
