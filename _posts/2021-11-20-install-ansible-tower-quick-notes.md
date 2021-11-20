---
layout: post
title: Install Ansible Tower quick notes
date: 2021-10-31T11:00:11.986Z
thumbnail: https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/Iset_Tower.jpg/480px-Iset_Tower.jpg
---
Use Red Hat Enterprise v7 / Centos 7 or higher OS

OS disk partitions
/var, /var/tmp, and /tmp

Use a dedicated /var partition

Install Ansible Tower

```wget -nd https://releases.ansible.com/ansible-tower/setup/ansible-tower-setup-latest.tar.gz
 tar zxvf ansible-tower-setup-latest.tar.gz```

Edit the inventory yaml file at set required password parameters

For more information please see:
https://docs.ansible.com/ansible-tower/3.6.3/html/quickinstall/install_script.html





