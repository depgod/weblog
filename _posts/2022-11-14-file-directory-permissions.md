---
layout: post
title: File Directory Permissions
tags: linux
---

# File and Directory Permissions
Understanding read, write and executable permissions.  


If we do `ls -l`:  
```bash
$ .rw-rw-r-- user family 168 B  Sun Nov 13 01:59:08 2022 things.txt
```
Here as we can see a dot "." at the head part of the output line shows that this is a regular file.

When going through permissions there are four parts of it which can be seen in form of `drwx-rw-r--`.  


![alt text](./Linux-File-Permissions-2.webp)


r --> Read permission  
w --> Write permission  
x --> Executing permission  
"-" --> No permission


### More Important notation for file types
|File Type | Identifier|
-- | -- 
|Directory | d|
|Regular File | - , .|
|Character File | c|
|Link | l|
|Socker File | s|
|Pipe | p|
|Block Device | b|


### How permissions are evaluated

When a user tries to read or write to a file, the users permisisons are evaluated in a linear left to right manner:    
1. First owner permissions will be looked at and action will be taken based on its permissions.  
2. If the owner has none of the required permissions then group permissions will be looked at and action is taken accordingly.  
3. Lastly if the user is not int he group or does not exist then last set of permissions will be looked at and action is taken accordingly.  

