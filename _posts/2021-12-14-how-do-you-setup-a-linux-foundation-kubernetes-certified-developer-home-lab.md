---
layout: post
title: How do you setup a Linux foundation Kubernetes certified developer home lab?
date: 2021-12-14T19:37:00.485Z
thumbnail: https://en.wikipedia.org/wiki/File:Kubernetes_logo_without_workmark.svg
---
## How do you setup Kubernetes certified developer home lab with virtual machines? ##

You can use Ubuntu Multipass snap to quickly setup multiple virtual machines for a Kubernetes certified developer course home lab. This will save you expenses if you can run the lab at home.

### What components do you need? ###
* A home Linux machine capable of running Snap packages.
* Snapd for installing snap packages
* Multipass for setting up multiple virtual machines

### How much memory do you need? ###
Probably at least 24GB+, each virtual machine requires 8GB and you need to have memory for your Linux machine

Install Snapd for installing snap packages.

`sudo apt install snapd`

Install Multipass via snap install

`sudo snap install multipass`

### How do you setup SSH keys for SSH into multipass machines? ###

Create a cloud-init.yaml file. Paste your public ssh key from ~/.ssh/id_rsa.pub on the first ssh_authorized_keys - line in the cloud-init.file.

cloud-init.yaml
```
ssh_authorized_keys:
- ssh-key xyz
```
Setup two Multipass virtual machines suitable for Linux foundation certified kubernetes lab. These virtual machines needs at least two cores -c 2, -d 20GB of disk and -m 8GB of memory.

`multipass launch -c 2 -d 20G -m 8G -n master --cloud-init ./cloud-init.yaml`

`multipass launch -c 2 -d 20G -m 8G -n worker --cloud-init ./cloud-init.yaml`

### How do you start the multipass virtual machines? ###
`multipass start master`

`multipass start worker`

### How do you SSH into the multipass virtual machines? ###
 
Use multipass list to get the ip adress of the master and worker nodes.


`multipass list`
```
Name                    State             IPv4             Image
master                  Running           10.170.11.105    Ubuntu 20.04 LTS
                                          192.168.242.64
worker                  Running           10.170.11.210    Ubuntu 20.04 LTS
```

Then use ssh with ubuntu@masterip ssh@workerip such as:

`ssh ubuntu@10.170.11.105`

`ssh ubuntu@10.170.11.210`

You now have two Ubuntu home virtual machines suitable for the labs.