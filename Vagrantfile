Vagrant.configure("2") do |config|
  config.vm.box = "raring"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"

  # Forward a port from the guest to the host, which allows for outside
  # computers to access the VM, whereas host only networking does not.
  config.vm.network :forwarded_port, guest: 8888, host: 8888, 
    host_ip: "127.0.0.1", auto_correct: true

  config.vm.provider "virtualbox" do |v|
    v.name = "python3pylab"
    v.customize ["modifyvm", :id, "--memory", 1024]
  end

  $script = <<SCRIPT
  echo I am provisioning...
  date > /etc/vagrant_provisioned_at
SCRIPT
  config.vm.provision :shell, :inline => $script
end

