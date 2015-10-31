---
title: PERL5LIB problem when applying Oracle Database Version 12.1.0.1.13 Bundle Patch
layout: post
tags: oracle, windows
---

Small issue when applying BP 12.1.0.1.13 on a windows host.

If the PERL5LIB environment variable is set then the datapatch step to apply sql changes to the database will potentially fail if the PERL libraries being pointed to by PERL5LIB don't match what it expects.

I found this to be the case as a previous installation of the OEM agent12c had set up the PERL5LIB to point at it's version of PERL which was different to the databases version of PERL.

The workaround is to unset the environment variable in the command window :

`set PERL5LIB=`

and then the datapatch execution should run without a hitch.