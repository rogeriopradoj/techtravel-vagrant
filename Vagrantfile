# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  #config.vm.provision :shell, :inline => "/etc/init.d/networking restart"
  #config.ssh.private_key_path = "vagrant.pub"
  config.vm.box = "techtravel"
  # config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  #config.vm.boot_mode = :gui
  config.vm.network :hostonly, "192.168.33.10"
  config.vm.share_folder "Sites", "/var/www", "~/Sites"
  config.vm.share_folder ".ssh", "/home/vagrant/.ssh", "~/.ssh"
  # config.vm.customize ["modifyvm", :id, "--memory", "360]
  #config.vm.network :bridged
  # config.vm.forward_port 80, 8080
  config.vm.forward_port 22, 2222
  config.ssh.max_tries = 3
  config.ssh.timeout = 30
  # config.ssh.verbose = false
  # config.ssh.username = 'vagrant'
  config.ssh.forward_agent = true

  # config.ssh.private_key_path = "~/.ssh/vagrant"
  # config.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
  # Update the server
   config.vm.provision :chef_solo do |chef|
    chef.log_level = :error
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe("vagrant_main")
    # chef.data_bags_path = "databags"
   end

end
