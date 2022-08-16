# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Base VM OS configuration.
  config.vm.box = "debian/bullseye64"
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.ssh.insert_key = false

  config.vm.provider :libvirt do |v|
    v.memory = 512
    v.cpus = 1

  config.vm.provision "file", source: "~/.ssh/id_main.pub", destination: "~/.ssh/authorized_keys"
  config.ssh.private_key_path = ["~/.vagrant.d/insecure_private_key", "~/.ssh/id_main"]
  config.ssh.insert_key = false

  end

  # Define VMs
  boxes = [
    { :name => "app1", :ip => "192.168.5.10" },
    { :name => "www-in", :ip => "192.168.5.2" },
    { :name => "www-static", :ip => "192.168.5.5" },
    { :name => "prometheus", :ip => "192.168.5.20" }
  ]

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
      config.vm.network :private_network, ip: opts[:ip]

    end
  end

end
