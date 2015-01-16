---
layout: post
title: How to create large file on Linux
category: Linux
---

##The most efficient way to create large file
The first (and best) choice is [`fallocate -l 10G vm.img`](https://stackoverflow.com/questions/257844/quickly-create-a-large-file-on-a-linux-system/11779492#11779492)
`fallocate` is used for preallocate space for file, this command does not require IO operation to the data blocks, and not initialize the file.

The fastest way is `truncate -s 10G vm.img`, it creates a 'sparse file', which means the file is not actually allocated on the physical disk until be modified. Beacuse it's not really allocate space from the disk, so with this command can create any size of file, even more then the physical disk has.

The alternative way is use `dd if=/dev/zero of=vm.img bs=1 count=0 seek=10G`, it will initialize the file.


