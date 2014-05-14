# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define :web do |web|
    web.vm.box = "precise64"
    web.vm.box_url = "http://files.vagrantup.com/precise64.box"
    web.vm.network :private_network, ip: "10.33.33.33"
    web.vm.network :forwarded_port, guest: 80, host: 1234

    web.vm.hostname = "dev.416.bike"

    web.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end

    # web.vm.provision :ansible do |ansible|
    #   ansible.playbook = "build-app.yml"
    #   ansible.inventory_path = "hosts-vagrant"
    #   ansible.verbose = "vvvv"
    #   ansible.ask_sudo_pass = true

    #   # https://github.com/mitchellh/vagrant/issues/3096
    #   ansible.limit = 'all'
    # end

  end

  config.vm.provision "docker", images: ["ubuntu"]

end
