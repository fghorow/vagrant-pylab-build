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
    v.customize ["modifyvm", :id, "--memory", 1024]
	v.customize ["modifyvm", :id, "--cpus",
	    %x(awk "/^processor/ {++n} END {print n}" /proc/cpuinfo 2> /dev/null || \
		sh -c 'sysctl hw.logicalcpu 2> /dev/null || echo ": 2"' | \
		awk \'{print \$2}\').chomp ]
  end

  $script = <<SCRIPT
  echo I am provisioning...
  date > /etc/vagrant_provisioned_at
  su vagrant <<LEVEL2SCRIPT
  cd /vagrant
  ipython3 notebook --ip="*" --no-browser > /dev/null 2> /dev/null &
  disown
LEVEL2SCRIPT
SCRIPT
  config.vm.provision :shell, :inline => $script
end

