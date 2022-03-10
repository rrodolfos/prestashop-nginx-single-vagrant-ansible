Vagrant.configure("2") do |config|

  config.vm.define "prestashop" do |config|
    config.vm.network "private_network", ip: "192.168.33.13"

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = "2"
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.compatibility_mode = "2.0"
    #ansible.verbose = "v"
  end

  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "prestashop"
  config.vm.synced_folder "share", "/srv/share"
  #config.vm.synced_folder "../data", "/vagrant_data", type: "nfs"

end
