# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
BOX64_URL = 'http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provider "virtualbox" do |vb|
    # boot with headless mode
    vb.gui = false

    # assing virtual CPUs dinamycally
    cpus_host_machine = `awk "/^processor/ {++n} END {print n}" /proc/cpuinfo 2> /dev/null || sh -c 'sysctl hw.logicalcpu 2> /dev/null || echo ": 2"' | awk \'{print \$2}\'`.chomp.to_i
    cpus_vm = [cpus_host_machine/2, 1].max

    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", 256]
    vb.customize ["modifyvm", :id, "--cpus", cpus_vm]
    vb.customize ["modifyvm", :id, "--ioapic", "on" ]
  end


  config.vm.define "vagrant-vim" do |web|
    web.vm.box = "trusty64"
    web.vm.box_url = BOX64_URL
    web.vm.network "private_network", ip: "192.168.150.1"

    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "test/vagrant.yml"
    end
  end

end
