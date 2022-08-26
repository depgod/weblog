---
layout: post
title: Basic file archiving and compression on linux
---
  
  
1. **Archiving a file**  
	```bash
	$ tar -cvf filename.tar foldername/location  
		`-c` create  
		`-v` verbos output  
		`-f` set a filename/filelocation  
	```  

2. **Compressing a file**  
	a. To compress a file:  
	```bash
	$ gzip filename.tar    
	```  
  
	b. Show the file:  
	```bash
	$ ls  
	```  

3. **Extracting a compressed file**  
To unzip and extract a file:  
```bash
$ tar -xzvf filename.tar.gz    
```  

  

