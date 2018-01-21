---
title: Upgrading Oracle Linux 6 and 7 to UEK4
layout: post
tags: Linux UEK
---

Oracle recently announced the availabilty of Unbreakable Enterprise Kernel (UEK) Release 4 for Oracle Linux 6 and Oracle Linux 7 [Here](https://blogs.oracle.com/linux/entry/announcing_the_general_availability_of4)

Do the following to upgrade existing systems to UEK4:

OEL6 :

    mv public-yum-ol6.repo public-yum-ol6.repo.old
    wget http://public-yum.oracle.com/public-yum-ol6.repo
    vi public-yum-ol6.repo

In the section [ol6_UEKR4] change enabled=0 to enabled=1 and then run yum update and reboot

     yum update
    reboot

OEL7 is the same except for the first two steps where you download the OEL7 public yum details instead

    mv public-yum-ol6.repo public-yum-ol7.repo.old
    wget http://public-yum.oracle.com/public-yum-ol7.repo
