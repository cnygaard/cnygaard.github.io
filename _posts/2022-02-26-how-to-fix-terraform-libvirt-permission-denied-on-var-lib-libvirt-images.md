---
layout: post
title: How to fix Terraform libvirt permission denied on /var/lib/libvirt/images
date: 2022-02-26T14:24:43.101Z
thumbnail: https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2Fthumb%2F7%2F70%2FKvmbanner-logo2_1.png%2F225px-Kvmbanner-logo2_1.png&f=1&nofb=1
---
If when running Terraform Libvirtd driver you get a permission denied
when trying to open a disk image file in /var/lib/libvirtd/images. Here is 
instructions on to fix that.

Error message will be similar to: "Could not open '/var/lib/libvirt/images/disk_image.raw': Permission denied')"

Fix: 

Please add the following lines for *.qcow and *.raw in file /etc/apparmor.d/libvirt/TEMPLATE.qemu 

contents of /etc/apparmor.d/libvirt/TEMPLATE.qemu 
```bash
#
# This profile is for the domain whose UUID matches this file.
#

#include <tunables/global>

profile LIBVIRT_TEMPLATE flags=(attach_disconnected) {
  #include <abstractions/libvirt-qemu>
   /var/lib/libvirt/images/**.qcow2 rwk,
   /var/lib/libvirt/images/**.raw rwk,
}
```

After adding the config file line in /etc/apparmor.d/libvirt/TEMPLATE.qemu please
restart the libvirtd systemd service.

Systemd restart libvirtd command
```bash
sudo systemctl restart libvirtd
```