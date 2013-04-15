Vagrant::Config.run do |config|
  config.vm.define :python3pylab do |python3pylab_config|
    # Every Vagrant virtual environment requires a box to build off of.
    python3pylab_config.vm.box = "precise64"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    python3pylab_config.vm.box_url = "http://files.vagrantup.com/precise64.box"

    # Forward a port from the guest to the host, which allows for outside
    # computers to access the VM, whereas host only networking does not.
    python3pylab_config.vm.forward_port 8888, 8888, :auto => true

    $script = <<SCRIPT
    set -e
    export DEBIAN_FRONTEND=noninteractive
    echo I am provisioning...
    date > /etc/vagrant_provisioned_at
    cp /etc/apt/sources.list /etc/apt/sources.list.old.pylab
    echo deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse > /etc/apt/sources.list
    echo deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse >> /etc/apt/sources.list
    echo deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe multiverse >> /etc/apt/sources.list
    echo deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe multiverse >> /etc/apt/sources.list
    echo >> /etc/apt/sources.list
    cat < /etc/apt/sources.list.old.pylab >> /etc/apt/sources.list
    aptitude -y update
    aptitude -y full-upgrade
    aptitude -y install build-essential
    aptitude -y install python3
    aptitude -y install python3-dev
    aptitude -y install curl
    aptitude -y install cmake
    aptitude -y install libzmq-dev
    aptitude -y install libqt4-dev
    aptitude -y install libqt4-opengl-dev
    aptitude -y clean
	aptitude -y autoclean
    curl http://python-distribute.org/distribute_setup.py | python3
    curl https://raw.github.com/pypa/pip/master/contrib/get-pip.py | python3
    pip-3.2 install pyside
SCRIPT
    python3pylab_config.vm.provision :shell, :inline => $script
    python3pylab_config.vm.action("reload")
    $script = <<SCRIPT
    dd if=/dev/zero of=/zero.pylab bs=2048
    sync
    rm /zero.pylab
SCRIPT
    python3pylab_config.vm.provision :shell, :inline => $script
  end
end
