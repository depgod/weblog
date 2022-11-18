---
layout: page
title: Setup static ip on ubuntu-server
tags: networking
---
## Tutorial
  
**Using netplan**  
  
1. First checkout your interface name:  
```bash
$ ip a  
```  
Image
2. Now edit your netplan config file:  
```bash
$ sudo nano /etc/netplan/netplan-config.yaml  
```  
3. Now enter the following:  
```bash
$ network:  
  version: 2  
  rendered: networkd  
  ethernets:  
    [interface name]:  
      dhcp4: no  
      addresses:   
        - 192.168.1.10/24  
      gateway4: 192.168.1.1  
      nameservers:  
        addresses:   
        - 8.8.8.8  
        - 8.8.4.4  
        - 8.8.4.4  
```  
Here we have disabled DHCP and given a local ip with gateway and nameservers.  
__NOTE: YAML files are highly space sensitive.__  

4. After saving the above file:
```bash
$ sudo netplan try netplan-config.yaml
```
This will test the configuration and will ask to revert to default if some error is seen.  

