---
layout: post
title: Fucking the GFW with VPC
category: GFW
---
The GoAgent become more and more unstable, should consider other way to fucking the GFW.
Using VPC is a choice.
The [openshift](https://developers.openshift.com/) provide **free** VPC srevice.

The basic function is use the VPC to do SSH proxy.

To access the Openshift VPC with SSH, requires the `git`, `ruby` and `rhc` toolchain. Follow the [How to access the openshift with ssh](https://developers.openshift.com/en/managing-remote-connection.html) to install necessary packages first. Sometimes when install the `rhc` will failed, just try more times.

If your app name is 'python', access the openshift with the following command: 

```sh
rhc ssh python
```

#Issue
Use Bitvise SSH Client to access the VPC failed, because the ssh-key not correct set.

#Reference
[Using openshift to fucking the GFW](http://skaypo.blogspot.com/2013/08/openshift-ssh.html)
[install gem return 'certification verify failed'](http://stackoverflow.com/questions/19745960/unable-to-install-any-gem-by-ruby-in-windows)

