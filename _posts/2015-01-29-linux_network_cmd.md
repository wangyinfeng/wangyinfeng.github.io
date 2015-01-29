---
layout: post
title: Commands to check networking status on Linux
category: Linux
---
Check the ARP table

```sh
[root@localhost ~]# arp -e
Address                  HWtype  HWaddress           Flags Mask            Iface
9.111.77.1               ether   00:00:5e:00:01:0d   C                     br0
10.10.10.11              ether   6c:ae:8b:7e:77:f8   C                     eth0
169.254.95.118           ether   5c:f3:fc:15:14:66   C                     usb0
```

Check the FDB of bridge

```sh
[root@localhost ~]# brctl showmacs brX
port no mac addr                is local?       ageing timer
  5     52:54:00:07:fc:dc       no                15.29
  3     52:54:00:92:6b:b1       no               224.02
  4     52:54:00:fd:ba:ab       no                15.29
  5     fe:54:00:07:fc:dc       yes                0.00
  2     fe:54:00:14:88:63       yes                0.00
  1     fe:54:00:36:66:5d       yes                0.00
  3     fe:54:00:92:6b:b1       yes                0.00
  4     fe:54:00:fd:ba:ab       yes                0.00
```

Check the RIB

```sh
[root@localhost ~]# ip route show 
169.254.95.0/24 dev usb0  proto kernel  scope link  src 169.254.95.120  metric 1 
10.10.10.0/24 dev eth0  proto kernel  scope link  src 10.10.10.21 
9.111.77.0/24 dev br0  proto kernel  scope link  src 9.111.77.66 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 
169.254.0.0/16 dev eth0  scope link  metric 1002 
default via 9.111.77.1 dev br0 
```

Check the FIB

```sh
[root@localhost ~]# ip route show cache
local 169.254.95.120 from 169.254.95.118 dev lo  src 169.254.95.120 
    cache <local,src-direct>  iif usb0
local 10.10.10.21 from 10.10.10.11 dev lo  src 10.10.10.21 
    cache <local,src-direct>  iif eth0
local 9.111.77.66 from 9.110.41.25 dev lo  src 9.111.77.66 
    cache <local>  iif br0
10.10.10.11 from 10.10.10.21 dev eth0 
    cache  mtu 1500 advmss 1460 hoplimit 64
9.110.41.25 from 9.111.77.66 tos lowdelay via 9.111.77.1 dev br0 
    cache  mtu 1500 advmss 1460 hoplimit 64
169.254.95.118 dev usb0  src 169.254.95.120 
    cache  mtu 1500 advmss 1460 hoplimit 64
169.254.95.118 from 169.254.95.120 dev usb0 
    cache  ipid 0x3a3b mtu 1500 advmss 1460 hoplimit 64
```

FIB is a subet of RIB, cache for the most frequency used paths.

#Reference
[ip route](http://linux-ip.net/html/tools-ip-route.html#tools-ip-route-flush-cache)

