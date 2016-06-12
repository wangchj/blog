---
layout: post
status: publish
published: true
title: Lubuntu 14.04 Wireless Network Manager
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 659
wordpress_url: http://codenuggets.com/?p=659
date: '2014-04-18 18:57:45 -0500'
date_gmt: '2014-04-18 18:57:45 -0500'
categories:
- OS
- Lubuntu
tags:
- Linux
- Lubuntu
- Lubuntu 14.04
- wireless network
- bug
comments:
- id: 2820
  author: Max
  author_email: massimo.scarlassare@gmail.com
  author_url: ''
  date: '2014-05-01 07:18:22 -0500'
  date_gmt: '2014-05-01 07:18:22 -0500'
  content: Same problem. I use nm-applet to run wireless connection
- id: 2882
  author: Alex
  author_email: alexander.lenail@tufts.edu
  author_url: ''
  date: '2014-05-12 21:32:39 -0500'
  date_gmt: '2014-05-12 21:32:39 -0500'
  content: How do you use nm-applet? It just puts up a little bubble in the top left
    that disappears on click. "Using fallback from indicator to DtoStatusIcon"
- id: 2884
  author: Jeff
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-05-12 22:10:37 -0500'
  date_gmt: '2014-05-12 22:10:37 -0500'
  content: Hi Alex, after entering the command `nm-applet` in terminal,
    I’d get the applet’s icon, that look like signal bars, in the system tray at the
    lower right corner of the screen, indicating the available wireless networks.
    Let me know if this helps!
- id: 3262
  author: Andy
  author_email: andycg2010@gmail.com
  author_url: ''
  date: '2014-07-27 02:23:24 -0500'
  date_gmt: '2014-07-27 02:23:24 -0500'
  content: Was having problems as well, opened up terminal, typed that in and blam!
    Working. Thank you so much!
- id: 3298
  author: Jeff
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-08-01 21:07:23 -0500'
  date_gmt: '2014-08-01 21:07:23 -0500'
  content: I'm glad it worked for you!
- id: 3808
  author: larry
  author_email: lneffneff@hotmail.com
  author_url: ''
  date: '2014-10-24 04:05:10 -0500'
  date_gmt: '2014-10-24 04:05:10 -0500'
  content: "Total newbie here, this also worked for me after searching threads for
    hours!  Thank you.\r\n\r\nCould someone tell me how to keep the icon in the system
    tray.  Mine always disappears.  Thanks you"
- id: 3831
  author: Jeff
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-10-27 14:37:01 -0500'
  date_gmt: '2014-10-27 14:37:01 -0500'
  content: My icon does not stay in the system tray, but network still works. You
    can run `nm-applet` again to get the system icon.
- id: 4690
  author: LEON
  author_email: Leon.cooper@hotmail.co.uk
  author_url: ''
  date: '2015-07-05 15:38:42 -0500'
  date_gmt: '2015-07-05 15:38:42 -0500'
  content: "HI there trying to save my parents time by installing Lubuntu. Everything
    is fine apart from the  wireless. If i type in nm-applet  I get this\r\n\r\n**
    (nm-applet:1850): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown:
    The name org.a11y.Bus was not provided by any .service files\r\n\r\n(nm-applet:1850):
    nm-applet-WARNING **: Failed to register as an agent: (32) An agent with this
    ID is already registered for this user.\r\nnm-applet-Message: using fallback from
    indicator to GtkStatusIcon\r\n\r\nAny help would be much appreciated!!!!"
- id: 5254
  author: Ehren
  author_email: iceenl@yahoo.com
  author_url: ''
  date: '2015-12-05 09:21:18 -0600'
  date_gmt: '2015-12-05 09:21:18 -0600'
  content: My network panel only gives me the option to connect to a VPN. No Wireless
- id: 5255
  author: Ehren
  author_email: iceenl@yahoo.com
  author_url: ''
  date: '2015-12-05 09:22:23 -0600'
  date_gmt: '2015-12-05 09:22:23 -0600'
  content: It shows two computers with a gray X next to them.
- id: 5390
  author: Eli perkins
  author_email: saltsrox7@gmail.com
  author_url: ''
  date: '2016-01-09 22:31:08 -0600'
  date_gmt: '2016-01-09 22:31:08 -0600'
  content: "when I type it I just get \r\n**(nm-applet:2771): CRITICAL **: nm_secret_agent_register:
    assertation 'priv->registered == FALSE' failed\r\nnm-applet-Message: using
    fallback from indicator to GtkStatusicon\r\n\r\n\r\nPlease help im new to linux"
---
Yesterday I did a fresh install of the latest of Lubuntu 14.04 on my HP netbook. Initially, I have used Lubuntu 13.04.

My initial impression is that the OS is more polished, but I ran into a problem that the Wireless Network Applet is no longer present on the taskbar. This gives me 2 problems:

1. The system no longer connect to the wireless at Auburn University (AU_Wifi).
2. I can't change wireless network to connect to

Apparently, there is a bug in the new system and is documented <a href="http://askubuntu.com/questions/449709/network-indicator-disappeared-in-lubuntu">here</a>. What I did was just manually run the network applet as follows:

```
nm-applet
```