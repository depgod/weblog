---
layout: post
title: Setting Exact Permissions
tags: linux
---

# Setting Exact Permissions

Just like while adding or removing permissions we can set exact permissions using the "=" sign insted of "+"/"-".

### Important notations  

| | Option | Permission |
--|--|--
|user | u= | u=w / u=rw / u=rwx |
|group | g= | g=w / g=rw / g=rwx |
|others | o= | o=w / o=rw / o=rwx |



__Example__:
Suppose we want to give a group permanant permission to read, we will do it like this:  
```bash
$ chmod g=r family_dog.jpg
```

Now if we do `ls -l`:  
```bash
$ -r--r-----. 1 aaron family 49 Oct 27 14:41 family_dog.jpg 
```
Here we can see that though we gave the group exact read permission so now family will only have read permissions for the file.

No what if we use "g=" empty, this basically says to give all the empty permissions to the group which will result as:  
```bash
$ -r--------. 1 aaron family 49 Oct 27 14:41 family_dog.jpg
```

Here we see all group permissions gone because we set "g" to no permission.  


or we can also do the same thing by:  
```bash
$ chmod g-rwx family_dog.jpg
```

This will also do the same job as the previous one.
