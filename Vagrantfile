Vagrant.configure(2) do |config|

  config.vm.define "helpcase" do |helpcase|
      helpcase.vm.box = "ubuntu/trusty64"
      helpcase.vm.hostname = "helpcase.dev"
      helpcase.vm.network :private_network, ip: "192.168.33.102"
      helpcase.vm.network "forwarded_port", guest: 9200, host: 9200
      helpcase.vm.network "forwarded_port", guest: 5601, host: 5601

      helpcase.hostsupdater.aliases = ['office.yii2.helpcase', 'api.yii2.helpcase', 'yii2.helpcase']

      helpcase.vm.provision :ansible do |ansible|
          ansible.playbook = "provisioning/playbook.yml"
      end
  end
  
  config.vm.synced_folder "./backend", "/var/www/backend", id: "vagrant-root",
      owner: "root",
      group: "www-data",
      mount_options: ["dmode=775,fmode=775"]

  config.vm.synced_folder "./data", "/data"

  config.vm.provider "virtualbox" do |v|
      v.memory = 4024
      v.cpus = 2
  end

end
