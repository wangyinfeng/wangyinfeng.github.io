---
layout: post
title: All about zombie process
category: Linux
---
“如何杀死一个zombie进程？”今天做一个面试的时候被问到这样一个问题。杀进程知道，僵尸进程也知道，如何杀一个僵尸进程，这个确实不知道。

##什么是zombie进程
每个进程在生存过程中都会有zombie状态（init是例外？），通常进程在执行完毕退出时，其状态即为zombie，而后其parent进程通过调用`wait()`读取该进程的exit状态，清除该子进程。如果parent进程没有能够调用`wait()`清理子进程，那该进程实例就留在系统的进程表中，成为zombie进程。

zombie进程基本不占用内存和cpu资源，但由于系统的进程号是有限的，特别是在32位系统上，且zombie进程的出现即意味着潜在的问题。

##如何杀呢
zombie process之所以称为zombie，就是因为已经不live了，杀一个已死的process，逻辑上是不可能的。所以说要destroy比较合适。
zombie process既然存在，说明程序设计存在问题，或进程管理存在问题，应该从这些方面去查找原因为什么会产生这样的zombie，而不是简单地destroy。

如果非要destroy的话，方法有：  
 - kill该进程的parent进程，该zombie进程会成为orphan进程被init接管，init会定期call `wait()` 清理orphan进程。所以如果查看系统中有进程以zombie状态长期存在的话，说明其parent进程长期没有结束，也许存在问题。
 - 发送SIGCHILD给parent进程`kill -s SIGCHILD PPID`，parent进程call `wait()` 进行清理。

#Reference
[zombie process](http://en.wikipedia.org/wiki/Zombie_process)
[How to kill zombie process](http://stackoverflow.com/questions/16944886/how-to-kill-zombie-process)
[zombie vs orphan](http://stackoverflow.com/questions/20688982/zombie-process-vs-orphan-process)

