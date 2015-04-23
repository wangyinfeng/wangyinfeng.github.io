---
layout: post
title: All about zombie process
category: Linux
---
“如何杀死一个zombie进程？”今天做一个面试的时候被问到这样一个问题。杀进程知道，僵尸进程也知道，如何杀一个僵尸进程，这个确实不知道。

##什么是zombie进程
##为什么会有zombie进程
##如何杀呢
zombie process之所以称为zombie，就是因为已经不live了，杀一个已死的process，逻辑上是不可能的。所以说要destroy比较合适。
zombie process既然存在，说明程序设计存在问题，或进程管理存在问题，应该从这些方面去查找原因为什么会产生这样的zombie，而不是简单地destroy。

如果非要destroy的话，方法有：  
 - kill该进程的parent进程
 - 等待，等该zombie进程被init接管，init会定期清理zombie进程
 - 发送SIGCHILD给parent进程

#Reference

