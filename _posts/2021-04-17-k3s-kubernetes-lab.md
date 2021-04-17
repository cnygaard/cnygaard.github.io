---
layout: post
title: K3S Kubernetes lab
date: 2021-04-17T18:52:26.308Z
thumbnail: https://kubernetes.io/images/nav_logo.svg
---
This Lab installs K3d which is a dockerized version of Kubernetes on Debian

### Install Docker on Debian ###

```  
  sudo apt-get remove docker docker-engine docker.io containerd runc
  sudo apt-get update
  sudo apt-get install     apt-transport-https     ca-certificates     curl     gnupg     lsb-release
  curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
  sudo apt-get update
  sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### Install K3s ###

```
wget -nd https://github.com/rancher/k3d/releases/download/v4.4.1/k3d-linux-amd64
chmod 755 k3d-linux-amd64
mv k3d-linux-amd64 /usr/local/bin/k3d
```

### Create K3d Kubernetes Kluster ###

Create Kubernetes cluster with K3d
```
   sudo k3d cluster create
```
List kluster
```
sudo k3d cluster list

NAME          SERVERS   AGENTS   LOADBALANCER
k3s-default   1/1       0/0      true
```

### Copy Kubernets CLI config ###

```
sudo cp /root/.kube/config .kube/config
```
### Install Linkerd CLI ###

```
wget -nd https://github.com/linkerd/linkerd2/releases/download/stable-2.10.1/linkerd2-cli-stable-2.10.1-linux-amd64
```

Make linkerd executable

```
chmod 755 linkerd2-cli-stable-2.10.1-linux-amd64
```

Move linkerd to /usr/local/bin to be in search path $PATH

```
sudo mv linkerd2-cli-stable-2.10.1-linux-amd64 /usr/local/bin/linkerd
```

### Validate Kubernetes cluster for Linkerd ###

```
linkerd check --pre
```

### Install Linkerd control plane ###

```
linkerd install | kubectl apply -f -
```

### Check that Linkerd is installed correctly
```
linkerd check
```

### Install Linkerd Viz extension ###

```
linkerd viz install | kubectl apply -f - # on-cluster metrics stack
```

### Install Linkerd optional components ###
```
linkerd jaeger install | kubectl apply -f - # Jaeger collector and UI
linkerd multicluster install | kubectl apply -f - # multi-cluster components
```