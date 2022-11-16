---
layout: post
title: Setup ssh key based authentication
tags: linux
---
# Tutorial
  
--

## Pre-requisites    

1. Install the `openssh-server` package using your package manager
	e.g. For Ubuntu or Debian:  
	```bash
	$ sudo apt install openssh-server
	```
  
2. Enable the ssh service  
	```bash
	$ sudo systemctl enable ssh 
	```
3. Start the ssh service  
	```bash
	$ sudo systemctl start ssh
	```   
  
## Important notes  
  
1. SSH key pairs are two cryptographically secure keys that can be used to authenticate a client to an SSH server. Each key pair consists of a public key and a private key.  

2. The private key is retained by the client and should be kept absolutely secret. Any compromise of the private key will allow the attacker to log into servers that are configured with the associated public key without additional authentication. As an additional precaution, the key can be encrypted on disk with a passphrase.  

3. The associated public key can be shared freely without any negative consequences. The public key can be used to encrypt messages that only the private key can decrypt. This property is employed as a way of authenticating using the key pair.  

4. The public key is uploaded to a remote server that you want to be able to log into with SSH. The key is added to a special file within the user account you will be logging into called `~/.ssh/authorized_keys`.  

5. When a client attempts to authenticate using SSH keys, the server can test the client on whether they are in possession of the private key. If the client can prove that it owns the private key, a shell session is spawned or the requested command is executed.  

--

### Creating ssh keys  
  
Creating a ssh-keypair  
```bash
$ ssh-keygen
```  
1. This will generate a private and a public key for the system which will be id_rsa and id_rsa.pub respectively.  
2. At this step ssh will ask you for a different path to store the keys which can be defined by entering the path.  
3. It will also ask for a passphrase for better security.  
4. Now we will have two keys (private and public).  
5. You now have a public and private key that you can use to authenticate. The next step is to place the public key on your server so that you can use SSH key authentication to log in.  


### Copying ssh key to your server

Using `ssh-copy-id` copying the public key:  
```bash
$ ssh-copy-id username@ip_address
```  
Copying a specified key:  
```bash
$ ssh-copy-id -i <path> username@ip_address
```

### Authenticating to your server using ssh keys

Now we will connect using  
```bash
$ ssh username@ip_address
```  
- This will ask you to authenticate the user and it is the first time logging in and does not recognise the connection.  

### Disabling password authentication on your server
  
Now we will edit the `ssh_config` file for futher hardening  
1. Set `PasswordAuthentication no`  
2. Set `MaxAuthTries 4`  
3. Set `PubkeyAuthentication yes`  
4. Set `PermitEmptyPasswords no`  
5. Save and exit the config file.

### Final setps  
  
1. Restarting ssh  
```bash
$ sudo service ssh restart
```  

2. Enabling ssh  
```bash
sudo service ssh enable
```
	This will start the service on startup everytime.  

## ALL SET !!!  
