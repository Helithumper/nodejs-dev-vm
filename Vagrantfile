# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network :private_network, ip: "192.168.55.55"
  config.vm.synced_folder "~/", "/host"
  config.vm.hostname = "node.dev"
  # Configure VirtualBox.
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  # Enable provisioning with Ansible.
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.become = true
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
  end
end
