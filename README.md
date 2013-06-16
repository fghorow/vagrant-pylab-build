Well defined python 3 environment
=================================

**...for your server, your open source project and your collaborator.**

Define your environement (in rebuild-packages) and build it for vagrant and as ubuntu-chroot. 
Deploy them on your servers, create unit-test scripts that will never fail because of missing
dependencies and replace your development environment on the fly without breaking other
software your machine.

Python installed from dead snakes: https://launchpad.net/~fkrull/+archive/deadsnakes

vagrant-pylab-build
==================

Build and shrink a pylab environment for vagrant

* See https://github.com/ganwell/vagrant-pylab-build/blob/master/rebuild-packages 
  for packages installed.
* Use ./rebuild-vagrant to build the box.

Download
--------

https://dl.dropboxusercontent.com/u/170011615/python3pylab.box

````bash
vagrant box add pylab https://dl.dropboxusercontent.com/u/170011615/python3pylab.box
mkdir pylab
cd pylab
vagrant init pylab
vagrant up
````

**YOU NEED TO FIREWALL VBoxHeadless or the notebook and ssh port.**

-> The problem will be fixed with vagrant 1.2.3: https://github.com/Aigeruth/vagrant/commit/2979b0ad64593b1922d47e0db1a266c2aa026dfa
I will adapt this as soon as possible!

Browse http://localhost:8888 (or port displayed)

chroot-pylab-build
==================

If you want to install pylab on a server and skip virtual-box you can use the
chroot environment

* Its based on debootstrap so you need a debian or ubuntu system.
* Use sudo ./rebuild-chroot to build the pylab-chroot.

Download
--------

https://dl.dropboxusercontent.com/u/170011615/pylab3chroot.tar.xz

start-chroot
------------

* Either start the chroot from a user: ````bash
sudo ./start-chroot
````

* or at @reboot in roots crontab: 
````bash
@reboot HOME=/home/ganwell USER=ganwell /home/ganwell/prj/vagrant-pylab-build/start-chroot
````

