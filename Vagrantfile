Vagrant.configure("2") do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise64"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Forward a port from the guest to the host, which allows for outside
  # computers to access the VM, whereas host only networking does not.
  config.vm.network :forwarded_port, guest: 8888, host: 8888,
    auto_correct: true

  config.vm.provider "virtualbox" do |v|
    v.name = "python3pylab"
  end

  $script = <<SCRIPT
  echo I am provisioning...
  date > /etc/vagrant_provisioned_at
  ipython3 notebook --no-browser &
  disown
SCRIPT
  config.vm.provision :shell, :inline => $script
end

