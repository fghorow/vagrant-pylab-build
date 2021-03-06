Well defined python 3 environment
=================================

**...for your server, your open source project and your collaborator.**

Define your environement (in rebuild-packages) and build it for vagrant and as ubuntu-chroot. 
Deploy them on your servers, create unit-test scripts that will never fail because of missing
dependencies and replace your development environment on the fly without breaking other
software your machine.

Changes
-------

* 2013-08-12 Updated to raring, standard python3.3 and standard pyside
* 2013-08-12 Removed most of texlive doc making the image even smaller

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

Browse http://localhost:8888 (or port displayed)

chroot-pylab-build
==================

If you want to install pylab on a server and skip virtual-box you can use the
chroot environment

* Its based on debootstrap so you need a debian or ubuntu system.
* Use sudo ./rebuild-chroot to build the pylab-chroot.

Download
--------

https://dl.dropboxusercontent.com/u/170011615/python3pylab.tar.xz

start-chroot
------------

* Either start the chroot from a user: 
````bash
sudo ./start-chroot
````

* or at @reboot in roots crontab: 
````cron
@reboot HOME=/home/ganwell USER=ganwell /home/ganwell/prj/vagrant-pylab-build/start-chroot
````

sha256 sums
===========

````
$> openssl dgst -sha256 python3pylab.*
H256(python3pylab.box)= 76cf38fc5417f7179f3795876e0880604545c7aee87729f0a47ad01bf4c198ac
SHA256(python3pylab.tar.xz)= 35c1e2e6fc7ff092fd8e7e54e6b458bee1db6f9bfdeebc53833d90eb98596e72
````
