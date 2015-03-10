---
layout: post
title: Ping the 8.8.8.8 from a VM
category: OpenStack
---
Question: When `ping` from a VM to the destination `8.8.8.8`, describe the package flow.

If the VM NIC connect to the bridge device, and have public IP address, the package will go through the bridge then to the physical adapter directly.


#Reference


