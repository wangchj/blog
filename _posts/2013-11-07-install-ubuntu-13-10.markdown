---
layout: post
status: publish
published: true
title: Install Ubuntu 13.10
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 590
wordpress_url: http://codenuggets.com/?p=590
date: '2013-11-07 05:14:23 -0600'
date_gmt: '2013-11-07 05:14:23 -0600'
categories:
- Uncategorized
tags:
- Linux
- Ubuntu
- Cinnamon
- Ubuntu 13.10
- Cinnamon 2
- nVidia
- driver
- freeze
comments: []
---
I was trying to uninstall MySQL Workbench from the Ubuntu 13.04 machine at school and accidentally corrupted the entire system.

I decided to re-install the system with Ubuntu 13.10. After the installation from USB, I naturally went ahead and install Cinnamon from official ppa. Unfortunately, Cinnamon 2.0 is very unpolished on 13.10. The interface is inconsistent and a mess (also the folder icons are very ugly color). Also I was unable to log into Unity (the desktop manager came with Ubuntu) after installing Cinnamon.

So I re-install again without Cinnamon. The thing I notice about 13.10 is that it's default video driver is not compatible with my video card. After using it for a few minutes, it'd cause random freeze on my computer in which case I have to press my computer power button to turn off.

I have Dell Optiplex 960 with nVidia GeForce 9300 GE video card. I had to go into Ubuntu Software Center -> Edit menu -> Software Sources -> Additional Driver, and change from X.Org -- Nouveau driver to NVIDA binary Xorg driver nvidia-319 (proprietary, test) driver. And no more freezes.

