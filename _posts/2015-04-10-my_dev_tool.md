---
layout: post
title: The collection about my personal tools
category: Tool
---
Time to go, and time to collect the useful tools I got in the past years.

The best way maybe have a VPC or VM or Container to have all tools installed, and can be synchronized between different place, and can be copied/moved to anywhere, so this duplicated work doesn't need to do everytime when change the workstation or job.(Of course I don't want to change the next job too quickly)

#For general
##[Vim](http://www.vim.org/)
Vim is essential, the configuration file is located at 'github\shell'.
And the plugins...
###nerdtree
###cscope
###taglist
###netrw

#For Linux

#For OSX
##Xcode
The easy way to get the C compiler and git.
##[brew](brew.sh)

```sh
#replace the gem source with local provider
gem sources -r https://rubygems.org/
gem sources -a http://ruby.taobao.org/
gem sources -u
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

##rhc
RedHat Openshift tools, used to connect the VPS, to fucking the GFW.

To keep the ssh session alive, add `config` file under `~/.ssh/` with the content `ServerAliveInterval 60`, so every 60 seconds the client will send a sign-of-life signal to the server.

##pip

```sh
sudo easy_install pip
```

##Crypto library
The module name is 'crypto' on MAC, but 'Crypto' on others, so install the crypto module by pip will not work on MAC. Install the module by `easy_install` will be OK.

```sh
sudo easy_install -Z pycrypto
```

Install `autossh` to enable automatally reconnection when session drop:

```sh
brew install autossh
autossh -M 1081 -D 1080 -i /Users/w/.ssh/identification -qNnt 54b5fc@python-mfrc531.rhcloud.com
```

#For Windows
##[Chrome](http://www.google.com/chrome/)
Chrome Application Lanucher.
SwitchyOmega configuration files.
##[Bitvise SSH Clienta](http://www.bitvise.com/)
Connect to my VPC to fuck the GFW.
##[Evernote](https://evernote.com/)
##[MSYS](http://www.mingw.org/wiki/msys)
##[Git](https://github.com/)
##[VirtualBox](https://www.virtualbox.org/)
##[MinGW](http://www.mingw.org/)
##[UltraVNC](http://www.uvnc.com/)
##[Calibre](http://calibre-ebook.com/)
##[PuTTY](http://www.putty.org/)
##[FileZilla](https://filezilla-project.org/)
##SecureCRT
##[Wireshark](https://www.wireshark.org/)
##[Youdao Dict](http://dict.youdao.com/)
##[Foxit Reader](http://www.foxitsoftware.com/Secure_PDF_Reader/)
##[WPS Office](http://www.wps.com/)
##[Weiyun](http://www.weiyun.com/)

