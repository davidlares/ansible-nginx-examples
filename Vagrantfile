# vagrant block -> ruby syntax
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64" # OS selection
  # two machines, two static IPs
  config.vm.define "host_1" do |host|
    host.vm.network "private_network", ip: "10.0.0.100"
  end
  config.vm.define "host_2" do |host|
    host.vm.network "private_network", ip: "10.0.0.101"
  end
  # SSH keys are automatically generated, we disable it
  config.ssh.insert_key = false
  # OS keys set manually (local)
  config.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
  # Path for the SSH on the VM (file copied)
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
  # disable vagrant folder sync
  config.vm.synced_folder  ".", '/vagrant', disabled: true
end
