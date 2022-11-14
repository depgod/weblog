---
layout: post
title: Adding and removing Permissions
---

# Adding permissions

In order to change permissions of a file we can use specific options with the `chmod` command.  

### Important options

| | Option | Examples |
--|--|-- |
|user | u+ | u+w / u+rw / u+rwx |
|group | g+ | g+w / g+rw / g+rwx |
|others | o+ | o+w / o+rw / o+rwx |


__Example__:
```bash
> ls -l
-r--rw----. 1 aaron family 49 Oct 27 14:41 family_dog.jpg
```
Here we can see aaron has only read permission, what if we want to change this to read and write permissions both, we will use it like this:  
```bash
$ chmod u+w family_dog.jpg
```

and now if we do `ls -l`:  
```bash
$ -rw-rw----. 1 aaron family 49 Oct 27 14:41 family_dog.jpg
```

Now we see user aaron has write permission to the file.


# Removing permissions

Just as like in adding permissions we used `u+` or `g+` we will use `u-` or `g-`:  

| | Option | Examples |
--|--|--
| user | u- | u-w / u-rw / u-rwx |
| group | g- | g-w / g-rw / g-rwx |
| others | o- | o-w / o-rw / o-rwx |

__Example__:  
Here we can see that we are removing write permission from the user:  
```bash
$ chmod u-w family_dog.jpg
```
Now if we check by `ls -l` write permission is gone fromthe user:  
```bash
$ -r--rw----. 1 aaron family 49 Oct 27 14:41 family_dog.jpg
```


