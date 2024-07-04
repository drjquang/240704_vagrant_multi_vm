require 'yaml'

# Load the VM profiles from the YAML file
vm_profiles = YAML.load_file('vm_profiles.yml')

Vagrant.configure("2") do |config|
  vm_profiles['vms'].each do |vm|
    config.vm.define vm['name'] do |v|
      v.vm.box = vm['box']
      v.vm.hostname = vm['hostname']
      v.vm.network "public_network", ip: vm['public_ip']
      v.vm.network "private_network", ip: vm['private_ip']
      v.vm.provider "virtualbox" do |vb|
        vb.name = vm['name']
        vb.memory = vm['memory']
        vb.cpus = vm['cpus']
      end
    end
  end
end
