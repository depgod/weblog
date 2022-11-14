---
layout: post
title: Octal Permissions
---

# Octal Permissions

In order to understand octal permissions we need to use the `stat` command:  
```bash
$ stat family_dog.jpg
```
__Output__:
```bash
File: family_dog.jpg
  Size: 49		Blocks: 8		IO Block: 4096	regular file
Device: fd00h/64768d	Inode: 52946177		Links: 1
Access: (0640/-rw-r-----) Uid: ( 1000/	aaron)	Gid: (	10/	wheel)  
```

Here we can see the owner permission is 6, group permission is 4, and other permission is 0, but how do these numbers are calculated?  

To better understand the octal permissions we need to understand the binary table:  

__Example__:
As we can see in the above example about the rwx permissions, if we look closely:  
`-rw-r-----`  
1. `-rw`: shows 110
2. `r--`: shows 100
3. `---`: shows 000

Looking at the binary table:

| Binary | Decimal |
--|--
|000|0|
|001|1|
|010|2|
|011|3|
|100|4|
|101|5|
|110|6|
|111|7|


__Example__:
For another example lets see how we can use octal values to set permission for a file:  

Suppose we want to give read, write and executing permissions to the user how will the octal values look like?  
```bash
$ chmod 740 family_dog.jpg
```

We gave 7 as we wanted the user to have read, write and executing permissions and group had 4 means group had only read permission and others had 0 as per the binary table.  



