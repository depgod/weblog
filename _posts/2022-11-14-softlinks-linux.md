---
layout: post
title: Softlinks in linux
---

# Softlinks in linux

Softlinks are basically an absolute path to the executable, like in windows we see desktop shortcuts which actually leads to an absolute path of the executable resulting in executing that file upon clicking.

### Creating softlinks

```bash
$ ln -s path_to_target_file path_to_link_file
```

path_to_target_file -> original file  
path_to_link_file -> represents shortcut

### Viewing hard/softlinks

```bash
$ ls -l
```
__Output__:
```bash
$ lrwxrwxrwx root root     23 B  Sun Jul 17 00:48:34 2022  vtrgb ⇒ /etc/alternatives/vtrgb
```

Shows an example of a file in that directory.

### Reading hard/softlinks of a file

```bash
$ readlink family_dog_shortcut.jpg
```
Output:
```bash
$ /home/aaron/Pictures/family_dog.jpg
```
Shows hard and softlinks of mentioned file.

## Important points of softlinks

Softlinks can be made between file to file or dir to dir or even between different filesystems.
