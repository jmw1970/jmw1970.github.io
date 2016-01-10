---
title: Adding the EPEL yum repository to Oracle Linux 6 and 7
layout: post
tags: Linux EPEL
---

There are some useful utility programs available in the [Fedora Extra Packages for Enterprise Linux (EPEL) project]( https://fedoraproject.org/wiki/EPEL ), two packages I particularly find useful and always install are htop and rlwrap.

However the EPEL isn't automatically setup on OEL so to add it do the following :

OEL 6 :
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
rpm -ivh epel-release-latest-6.noarch.rpm

OEL 7 :
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -ivh epel-release-latest-7.noarch.rpm
