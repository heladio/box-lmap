dir = Dir.pwd
vagrant_dir = File.expand_path(File.dirname(__FILE__))

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu"
  config.vm.box_url = "ubuntu/trusty64"
  config.vm.hostname = "devLAMPhcr"

  # Map our "salt" directory in this project to "/srv/salt" on the
  # server
  config.vm.synced_folder "salt", "/srv/salt"
  # Map our "project" directory in this project to "/project"
  config.vm.synced_folder "salt", "/srv/salt"

  # Create a public network so we can access the server from other devices
  # on our network.
  config.vm.network "public_network", type: "dhcp"

  config.ssh.forward_agent = true
  config.vm.provider :virtualbox do |vb|
    vb.gui = true
  end


  # Forward ports to Apache and MySQL
  config.vm.network :forwarded_port, guest: 80, host: 8888
  config.vm.network :forwarded_port, guest: 3306, host: 8889

  config.vm.provision :shell, path: "provision.sh"
end
# End of Vagrant config.
