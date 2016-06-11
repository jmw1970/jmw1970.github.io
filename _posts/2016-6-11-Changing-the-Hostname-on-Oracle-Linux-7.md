---
title: Changing the Hostname on Oracle Linux 7
layout: post
tags: Linux UEK
---

It's fairly straightforward to change the hostname using hostnamectl :

 hostnamectl set-hostname localhost.localdomain

check the new value using :

 hostnamectl status
