---
layout: post
title: your name is not in the sudoers file
category: Linux
---
Don't know why this issue will happen, one minute before, I can do `sudo`. I guess some file be modified by accident or some command be execulated.

The fix is add your name to the `/etc/sudoer` file. To be able to edit the file, first need to reboot the system, goto the `Recover mode` and then select `Check all file system (will exit read only mode)`, then select `Drop to root shell prompt`, now you are the root, and can do any recovering as you wish.
The most easy way is do:

```sh
echo 'myname ALL=(ALL) ALL' >> /etc/sudoer
```
Then select `Resume normal boot`.

One of the reference article introduce the command `usermod`, but not work for me. Nothing changed when I run the command.

```sh
usermod -a -G root sysadmin
```

#Reference
[How to fix username is not in the sudoer file](https://github.com/blackyboy/Ubuntu-Linux-Stuffs/blob/master/How-to-fix-%E2%80%9Cusername-is-not-in-the-sudoers-file.-This-incident-will-be-reported%E2%80%9D-Error-In-Ubuntu.md)
[Another answer about this question](http://www.linuxforums.org/forum/red-hat-fedora-linux/144428-solved-not-sudoers-file-incident-will-reported.html)

