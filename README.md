fuzzy-playbook
==============

Vagrantfile example
==============

    VAGRANTFILE_API_VERSION = "2"
    
    Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    
      config.vm.box = "squeeze64.box"
      config.vm.box_url = "http://dl.dropbox.com/u/937870/VMs/squeeze64.box"
    
      config.vm.provision "ansible" do |ansible|
        ansible.verbose = "vv"
        ansible.playbook = "../fuzzy-playbook/playbook.yml"
      end
    
      config.vm.network "private_network", ip: "192.168.50.4"
      
      config.vm.synced_folder "~/proj/", "/proj/", nfs: true
      config.ssh.forward_agent = true
    end
