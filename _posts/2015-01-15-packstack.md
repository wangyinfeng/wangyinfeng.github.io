---
layout: post
title: Step to step to install OpenStack with packstack
category: C
---
Going to develop under OpenStack, deploy an OpenStack enviroment is the basic skill.

##Perpartion
- Configure the network adapter, add at least 2 adapters, and configure the DNS server, gateway etc, to make sure one of them can access the internet.
- Disable `SELINUX` by modify the file `/etc/selinux/config`.
- Replace the yum repository with local repository
 ```sh
 [root@openstack]#cd /etc/yum.repos.d/
 [root@openstack]#mv CentOS-Base.repo CentOS-Base.repo.bak
 [root@openstack]#wget http://mirrors.163.com/.help/CentOS-Base-163.repo
 [root@openstack]#mv CentOS-Base163.repo CentOS-Base.repo
 [root@openstack]#yum clan all
 [root@openstack]#yum makecache
 ```
- Install the [`RDO(Red Hat Distribution of OpenStack)`](https://openstack.redhat.com/Main_Page). RDO is "a freely available, community-supported distribution of OpenStack that runs on Red Hat Enterprise Linux, Fedora and their derivatives".
 ```sh
 [root@openstack]#yum install -y http://rdo.fedorapeople.org/rdo-release.rpm
 ```
 If the rdo distribution is not what you deseried, provide the full path:
 ```sh
 [root@openstack]#yum install https://repos.fedorapeople.org/repos/openstack/openstack-icehouse/epel-6/rdo-release-icehouse-4.noarch.rpm
 ```
- Install the `packstack`, it's a python script, located at `/usr/bin/packstack`. (what does `run_setup.main()` do?)
 ```sh
 [root@openstack]#yum install -y openstack-packstack
 ```

##Installation
The install package is a serials of python scripts, locate at `/usr/lib/python2.6/site-packages/packstack/`.

After successful install, get the username and password from the file:
```sh
[root@openstack ~]# cat keystonerc_admin 
export OS_USERNAME=admin
export OS_TENANT_NAME=admin
export OS_PASSWORD=38f9888e7ab9455e
export OS_AUTH_URL=http://9.111.77.68:5000/v2.0/
export PS1='[\u@\h \W(keystone_admin)]\$ '
```

##Un-installation
Use the following [script](http://tuxlabs.com/?p=82) to do the uninstall operation.
```sh
#!/bin/bash
 
# Warning! Dangerous step! Destroys VMs
for x in $(virsh list --all | grep instance- | awk '{print $2}') ; do
    virsh destroy $x ;
    virsh undefine $x ;
done ;
 
# Warning! Dangerous step! Removes lots of packages
yum remove -y nrpe "*nagios*" puppet "*ntp*" "*openstack*" \
"*nova*" "*keystone*" "*glance*" "*cinder*" "*swift*" \
mysql mysql-server httpd "*memcache*" scsi-target-utils \
iscsi-initiator-utils perl-DBI perl-DBD-MySQL ;
 
# Warning! Dangerous step! Deletes local application data
rm -rf /etc/nagios /etc/yum.repos.d/packstack_* /root/.my.cnf \
/var/lib/mysql/ /var/lib/glance /var/lib/nova /etc/nova /etc/swift \
/srv/node/device*/* /var/lib/cinder/ /etc/rsync.d/frag* \
/var/cache/swift /var/log/keystone /var/log/cinder/ /var/log/nova/ \
/var/log/httpd /var/log/glance/ /var/log/nagios/ /var/log/quantum/ ;
 
umount /srv/node/device* ;
killall -9 dnsmasq tgtd httpd ;
 
vgremove -f cinder-volumes ;
losetup -a | sed -e 's/:.*//g' | xargs losetup -d ;
find /etc/pki/tls -name "ssl_ps*" | xargs rm -rf ;
for x in $(df | grep "/lib/" | sed -e 's/.* //g') ; do
    umount $x ;
done
```

##Issues
###yum update report python verison error
```  
Error: Package: python-netaddr-0.7.12-1.el7.centos.noarch (openstack)
           Requires: python(abi) = 2.7
           Installed: python-2.6.6-52.el6.x86_64 (@base)
               python(abi) = 2.6
```  
The python used by CentOS 6.5 is 2.6 instead of 2.7, and due to lots of tools depends on the python so it's not possible to just unintall the python 2.6 then install the 2.7. The correct solution is not try to update the python from 2.6 to 2.7, the correct way is check any incorrect setting which require python 2.7.


###Repostory URL error
```sh
[root@openstack yum.repos.d]# yum makecache
openstack                                                                      | 2.9 kB     00:00     
http://repos.fedorapeople.org/repos/openstack/openstack-juno/epel-6/repodata/repomd.xml: [Errno 14] PYCURL ERROR 22 - "The requested URL returned error: 404 Not Found"
Trying other mirror.
Error: Cannot retrieve repository metadata (repomd.xml) for repository: openstack-juno. Please verify its path and try again
```
It's because the **baseurl** in the openstack.repo is not correct.
When install OpenStack with RDO, should be careful about the EPEL version, some distribution doesn't have proper EPEL support. For example, the **Juno** only has EPEL7, while **IceHouse** has both EPEL6 and EPEL7. Browse the `https://repos.fedorapeople.org/repos/openstack/` to confirm the EPEL version.

Because the host OS version is CentOS 6.5, which should use EPEL6, not EPEL7, and Juno not have EPEL6 supported, so I chose install OpenStack IceHouse instead of Juno.
```sh
[root@openstack /]# cat /etc/yum.repos.d/openstack.repo 
[openstack]  
baseurl=http://repos.fedorapeople.org/repos/openstack/openstack-icehouse/epel-6/
gpgcheck=0
```

####What's EPEL?
EPEL(Extra Packages for Enterprise Linux) is maintained by Fedora, the CentOS/RedHat need to use the correct EPEL versionr, beacause the binary packages are build with the system compiler and linked against all the libraries provided by the repository.
EPEL7 requires python 2.7, EPEL requires python 2.6.

