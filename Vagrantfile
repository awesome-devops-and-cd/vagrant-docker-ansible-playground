Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.box_check_update = true
  config.vm.boot_timeout = 600
  config.vm.synced_folder "../piggy-bank", "/piggy-bank"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y ansible
    cd /vagrant
    ansible-playbook provision-localhost.yml
  SHELL

  # config.vm.provision "ansible" do |ansible|
  #   ansible.playbook = "provision.yml"
  #   ansible.verbose = "v"
  #   ansible.extra_vars = {
  #     ansible_become: true,
  #     ansible_become_user: "root",
  #     ansible_python_interpreter: "/usr/bin/python3"
  #   }
  # end
end
