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
      config.vm.network :forwarded_port, guest: 3000, host: 3000
      config.vm.network :forwarded_port, guest: 8080, host: 8080
      config.vm.network :forwarded_port, guest: 5678, host: 5678
      config.vm.network :forwarded_port, guest: 8888, host: 8888
      config.vm.network :forwarded_port, guest: 4003, host: 4003
      config.vm.network :forwarded_port, guest: 4000, host: 4000
          
      config.vm.synced_folder "~/proj/", "/home/vagrant/proj/", nfs: true
      config.ssh.forward_agent = true
    end


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/PlugIN73/fuzzy-playbook/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

