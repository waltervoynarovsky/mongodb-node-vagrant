Vagrant.configure("2") do |config|
  config.vm.synced_folder "global/", "/home/vagrant/global"

    # Provisiing MongoDB
    config.vm.define "mongodb" do | mongodb |
      mongodb.vm.box = "starboard/ubuntu-arm64-20.04.5"
      mongodb.vm.synced_folder "env/mongodb/", "/home/vagrant/env/mongodb"
      
      mongodb.vm.provider "vmware_desktop" do |v|
          v.gui = true
          v.vmx["ethernet0.virtualdev"] = "vmxnet3"
      end
  
      mongodb.vm.provision "shell", inline: <<-SHELL
        systemctl disable apt-daily.service
        systemctl disable apt-daily.timer
        sudo apt remove unattended-upgrades -y
      SHELL
      mongodb.vm.provision "shell", path: "env/mongodb/script.sh"
    end




  # NODE APP CONFIG
  config.vm.define "node-app" do |node|
  node.vm.box = "starboard/ubuntu-arm64-20.04.5"
  node.vm.box_version = "20221120.20.40.0"
  node.vm.box_download_insecure = true
  node.vm.synced_folder "app/", "/home/vagrant/app/"
  node.vm.synced_folder "env/", "/home/vagrant/env/"
  

  node.vm.hostname = "nology.training"
  node.hostsupdater.aliases = {
      '172.16.251.130' => "nology.training",
  }

  node.vm.provider "vmware_desktop" do |v|
      v.ssh_info_public = true
      v.gui = true
      v.linked_clone = false
      v.vmx["ethernet0.virtualdev"] = "vmxnet3"
  end

  node.vm.provision "shell", inline: <<-SHELL
    systemctl disable apt-daily.service
    systemctl disable apt-daily.timer
    sudo apt remove unattended-upgrades -y
  SHELL
# node.vm.provision "shell", path: "env/nodeapp/script.sh"
# node.vm.provision "shell", inline: "echo `export DB_PATH=192.168.56.20` >> /etc/profile.d/myvars.sh", run: "always"
end

end


# # Vmware
# # --------------------------------------------------------------

# Vagrant.configure("2") do |config|
#   # Provisiing MongoDB

  
#   # Provisioning NodeJS App
#   config.vm.define "nodeapp" do |nodeapp|
#     nodeapp.vm.box = "spox/ubuntu-arm"
#     nodeapp.vm.network "private_network", ip: "192.168.56.10"
#     nodeapp.hostsupdater.aliases = ["nology.training"]
#     nodeapp.vm.provider "vmware_fusion" do |vb|
#       nodeapp.vm.synced_folder "app/", "/home/vagrant/app/"
#       nodeapp.vm.synced_folder "env/", "/home/vagrant/env"
#     end
#     nodeapp.vm.provision "shell", inline: <<-SHELL
#       systemctl disable apt-daily.service
#       systemctl disable apt-daily.timer
#       sudo apt remove unattended-upgrades -y
#     SHELL
#     nodeapp.vm.provision "shell", path: "env/nodeapp/script.sh"
#   end
# end

# # Virtual Box
# # --------------------------------------------------------------
# # Vagrant.configure("2") do |config|
# #   # Provisioning NodeJS App
# #   config.vm.define "nodeapp" do |nodeapp|
# #     nodeapp.vm.box = "generic/ubuntu2010"
# #     nodeapp.vm.network "private_network", ip: "192.168.56.10"
# #     nodeapp.hostsupdater.aliases = ["nology.training"]
# #     nodeapp.vm.provider "virtualbox" do |vb|
# #       nodeapp.vm.synced_folder "app/", "/home/vagrant/app/"
# #       nodeapp.vm.synced_folder "env/", "/home/vagrant/env"
# #     end
# #     nodeapp.vm.provision "shell", path: "env/nodeapp/script.sh"
# #   end
# # end
