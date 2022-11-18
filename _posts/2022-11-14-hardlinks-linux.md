---
layout: page
title: Hardlinks in Linux
tags: linux
---

# Hard Links in Linux

Hard links are links which points to an inode of a file.

## Now what are inodes ?

Inode is a number which is assigned to a file or folder as a universal identifier inside a system.
For example:

```bash
$ stat file.txt
```
__Output__:
```bash
  File: file.txt
  Size: 0         	Blocks: 0          IO Block: 4096   regular empty file
Device: 802h/2050d	Inode: 16255425    Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/ jetskar)   Gid: ( 1000/ jetskar)
Access: 2022-11-13 04:18:10.164573967 +0530
Modify: 2022-11-13 04:18:10.164573967 +0530
Change: 2022-11-13 04:18:10.164573967 +0530
 Birth: 2022-11-13 04:18:10.164573967 +0530
```

__Explanation__:
1. Under the Blocks attribute we see "Inode" which shows a specific number, this number is the original identifier of the file in the whole system.
2. Under inode there is information regarding the data's permissions and access time all of which is stored inside blocks of data.
3. When we create a file we store some information in it, we tell linux to store this information under a file name.



Major benifit from hardlinking is that a file can be accessed by multiple users at the same time without making two copies of it at different locations.


## Limitations to hardlinks in linux

1. Hardlinks can only be made for files to files and never directory to directory or file to directory or vice versa.
2. You cannot create hardlinks between different filesystems, for example creating a hardlink between your local disk and your external disk will not work.
3. While making hardlinks it is important to have apropriate permissions to access the file properly.


## Creating hardlinks:

```bash
$ ln /home/Jason/filename.jpg /home/araon/filename.jpg
```


