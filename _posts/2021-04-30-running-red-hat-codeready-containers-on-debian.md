---
layout: post
title: Running Red Hat CodeReady Containers on Debian
date: 2021-04-30T19:31:30.479Z
thumbnail: https://upload.wikimedia.org/wikipedia/commons/thumb/6/67/Kubernetes_logo.svg/1024px-Kubernetes_logo.svg.png
---
If you happen to run on a Debian/Ubuntu based system and want to run Red Hat CodeReady containers a local Openshift installation to develop software.
Here is how todo it.

There is an currently an permission issue that I ran into on Debian/Ubuntu based systems with KVM/Qemu being unable to create crc.qcow2 in $HOME/.crc. A workaround is to create /opt/crc and symlink it to $HOME/.crc

Create an /opt/crc dir and symlink it to your $HOME/.crc
```/bin/bash
sudo mkdir /opt/crc
sudo chown $USERNAME /opt/crc
ln -s /opt/crc $HOME/.crc
```

Download CodeReady Containers
```bash
wget -nd https://mirror.openshift.com/pub/openshift-v4/clients/crc/latest/crc-linux-amd64.tar.xz
```

```bash
tar xvf crc-linux-amd64.tar.xz
cd crc-linux-xyz-amd64
chmod 755 crc
sudo mv crc /usr/local/bin
```

Get a Pull secret from https://cloud.redhat.com/openshift/create/local

Without the /opt/crc symlink you will get:
```
Error creating machine: Error creating the VM: Error creating machine: Error in driver during machine start: virError(Code=1, Domain=10, Message='internal error: process exited while connecting to monitor: 2021-04-30T19:42:48.604994Z qemu-system-x86_64: -drive file=/home/chris/.crc/machines/crc/crc.qcow2,format=qcow2,if=none,id=drive-virtio-disk0,aio=threads: Could not open backing file: Could not open '/home/chris/.crc/cache/crc_libvirt_4.7.5/crc.qcow2': Permission denied')
```

With the ~/crc to /opt/crc symlink in place.

To setup CodeReady containers 

```/bin/bash
$ crc setup
...
Your system is correctly setup for using CodeReady Containers, you can now run 'crc start' to start the OpenShift cluster

```
To start CodeReady containers
```/bin/bash

$ crc start

INFO Operators are stable (3/3) ...               
INFO Adding crc-admin and crc-developer contexts to kubeconfig... 
Started the OpenShift cluster.

The server is accessible via web console at:
  https://console-openshift-console.apps-crc.testing

Log in as administrator:
  Username: kubeadmin
  Password: 

Log in as user:
  Username: developer
  Password: developer

Use the 'oc' command line interface:
  $ eval $(crc oc-env)
  $ oc login -u developer https://api.crc.testing:6443
```

