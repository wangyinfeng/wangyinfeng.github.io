---
layout: post
title: Fucking the GFW with VPC
category: GFW
---
The GoAgent become more and more unstable, should consider other way to fucking the GFW.
Using VPC is a choice. The basic idea is use the VPC to do SSH proxy.
The [openshift](https://developers.openshift.com/) provide **free** VPC srevice.
#Preparation 
- The 1st step is check the ssh keys under your `$HOME/.ssh`, make sure the public and private key exist.
- Then regist the account on Openshift, according to the user guide, create your application.
- Copy your public key to the [setting](https://openshift.redhat.com/app/console/settings), the try with the `rhc` tool to login the console.

#Proxy by putty client
- Useing the `PuTTY key generator` to **import** the public key(`id_rsa.pub`), then **save private key** with the `.ppk` suffix(*Don't know how it's possible to get the private key with the public key* ).
- Open the `PuTTY`, **hostname** input the full name and url for the VPC, '54b5fcb...........@python-mfrc531.rhcloud.com' for example(*Don't know how to get the username from the configure page, I get it when use `rhc` tool to login the VPC, the username will print on console*).
- Select the private key(id_rsa) under [Connection]->[SSH]->[Auth].
- Set the **source port** to the port you want to do proxy, for example 8888, and choice **Dynamic**.
- Try login the VPC, and if login successful,
- then set the 'SwitchyOmega', add new mode, set the **SOCKS Proxy** address '127.0.0.1' and the port '8888'.
- If everyting is ok, don't forget to save the current session.
- Enjoy.

#Proxy by Bitvise SSH client
The easy way to access the Openshift VPC with SSH is use the `rhc`, it requires the `git`, `ruby` and `rhc` toolchain. Follow the [How to access the openshift with ssh](https://developers.openshift.com/en/managing-remote-connection.html) to install necessary packages first. Sometimes when install the `rhc` will failed, just try more times.
If your app name is 'python', access the openshift with the following command: 

```sh
rhc ssh python
```
While the `rhc` tool is not necessary to access the VPC, it's ok to access with normal key/password, using `rhc` is just simple, do not need to remember the un-rememb-able username, just type the application name.

Using Bitvise is just similar with the PuTTY: 
- input the necessary info on the **Login** page, 
- the **initial method** select *public key*, and then clik the **client key** or **client key manager**, 
- **generate new** RSA key, 
- then **export** the *public key* as *OpenSSH format*,
- copy the exported public key to the openshift setting page,
- Then at the **login** page, select the **client key** with the new generated profile.
- Try and enjoy.

##SSH via HTTP proxy
Intra-net usually allow user access the internet only via http proxy, Bitvise allow SSH to the server via http proxy, on the front page, click the **Proxy setting**, set the proxy.


#Serve for Android phone
The key is let android have ssh client to connect the VPC and provide SOCKS proxy.
- Download the [sshtunnel](https://code.google.com/p/sshtunnel/) and install, `root` maybe requested.
- Set the server address, username, copy the private key to the phone, and select the key from the **key manager**.
- Try to connect the VPC, and if connection is successful,
- Select the **Proxy with SOCKS**, **Auto connection**, and select the app you allow to access the free world in **application proxy**
- Then enjoy.

#Issue
- PuTTY will auto exit because long time no interactive with the VPC.
- Don't understand why just import the private key `id_rsa` is not work. Why need to generate new pair of key.

#Reference
[Using openshift to fucking the GFW](http://skaypo.blogspot.com/2013/08/openshift-ssh.html)  
[install gem return 'certification verify  failed'](http://stackoverflow.com/questions/19745960/unable-to-install-any-gem-by-ruby-in-windows)  
[Using PuTTY and Chrome](http://www.itordie.com/?p=50)  
[Using private/public key to access SSH server with Bitvise](https://www.webhostinghero.com/using-ssh-keys-with-adobe-dreamweaver/)  
[Android using SSH Tunnel](http://www.chekiang.info/2014/04/22.html)  

