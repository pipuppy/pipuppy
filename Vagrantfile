Vagrant.configure("2") do |config|
  config.vm.define "control-machine" do |pp|
    pp.vm.box = "ubuntu/xenial64"
    pp.vm.box_check_update = false
    pp.vm.box_version = "20170303.1.0"
    pp.vm.synced_folder "./ansible", "/home/ubuntu/ansible"

    pp.vm.provider "virtualbox" do |vb|
      vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
      vb.gui = false
      vb.memory = "1024"
      vb.name= "control-machine"
    end

    pp.vm.provision "ansible_local" do |ansible|
      ansible.provisioning_path = "/home/ubuntu/ansible"
      ansible.inventory_path = "./inventory"
      ansible.verbose = "v"
      ansible.playbook = "./groundwork.yml"
      ansible.vault_password_file = "./.data/.vault_password"
      ansible.tags = "bootstrap"
      ansible.compatibility_mode = "2.0"
      ansible.version = "2.4.3.0"
    end
    system('echo abc')
  end
end