vagrant-pylab-build
===================

Build and shrink a pylab environment for vagrant

* See https://github.com/ganwell/vagrant-pylab-build/blob/master/rebuild for packages installed.
* User ./rebuild to build box.

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
