# 请为OpenStack Summit上的中国声音投票

深入理解跨地域多活Swift存储集群
----------------
A Close Look at the Behaviors of the Multi-Region Swift Clusters

https://www.openstack.org/summit/austin-2016/vote-for-speakers/presentation/8012 

简介：本文介绍了实现通过Swift实现双活、多活存储集群的一些经验和心得

联想集团如何凭借OpenStack实现业务创新
----------------
How OpenStack helps business innovation at Lenovo

https://www.openstack.org/summit/austin-2016/vote-for-speakers/presentation/7945

Save your money in a different way: A Framework for Dynamic Consolidation of VMs in Openstack Clouds
---------------
https://www.openstack.org/summit/austin-2016/vote-for-speakers/presentation/6832



A Swift-All-In-One in a few easy steps.

 1. `vagrant up`
 1. `vagrant ssh`
 1. `echo "awesome" > test`
 1. `swift upload test test`
 1. `swift download test test -o -`

This project assumes you have Virtualbox and Vagrant.

 * https://www.virtualbox.org/wiki/Downloads
 * http://www.vagrantup.com/downloads.html

running-tests
=============

You should be able to run most tests without too much fuss once SSH'ed into the
VM.

 1. `.unittests`
 1. `.functests`
 1. `.probetests`
 1. `vtox -e pep8`
 1. `vtox -e py27`
 1. `vtox  # run all gate checks`

localrc-template
================

A few things are configurable, see `localrc-template`.

 1. `cp localrc-template localrc`
 1. `vi localrc`
 1. `source localrc`
 1. `vagrant provision`
 1. `vagrant ssh`
 1. `rebuildswift`

ninja-dev-tricks
================

A few scripts are available to make your dev life easier.

 1. `vagrant up --provision` will bring up your VM in working order (useful
    when your VM is halted)
 1. `source localrc; vagrant provision` on your host to push the new Chef bits
    in place (useful if you change localrc)
 1. `rebuildswift` to reapply everything like it would be at the end of Chef
    time (useful to revert local config changes)
 1. `resetswift` will wipe the drives and leave any local config changes in
    place (useful just to clean out Swift data)
 1. `reinstallswift` will make sure all of the bin scripts are installed
    correctly and restart the main swift processes (useful if you change
    branches)
 1. `autodoc [swift-specs]` will build the sphinx docs and watch files for
    changes, and upload them to a public container on your vm so you can
    review them
 1. `vtox` will hack the local tox.ini and setup.py so you can run tox tests
    successfully on the swift repo in the `/vagrant` directory
