---
layout: post
status: publish
published: true
title: Ubuntu 14.04 Brightness Control Issue
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 732
wordpress_url: http://codenuggets.com/?p=732
date: '2014-05-16 03:52:23 -0500'
date_gmt: '2014-05-16 03:52:23 -0500'
categories:
- OS
- Ubuntu
tags:
- bug
- Ubuntu 14.04
- brightness
comments:
- id: 3297
  author: tArKi
  author_email: djtark@gmail.com
  author_url: ''
  date: '2014-08-01 15:56:50 -0500'
  date_gmt: '2014-08-01 15:56:50 -0500'
  content: "Using Ubuntu 14.04 in an Asus S301 laptop, I can change the brightness
    going to \"Brightness & lock\" application but I cannot change it by pressing
    FN+F5/F6\r\n\r\nAlthough I really appreciate that you posted this solution, it
    didn't work for me and I'm still not able to use the function keys to change the
    brightness\r\n\r\nAny other idea?\r\n\r\nRegards!"
- id: 3310
  author: Jeff
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-08-03 15:01:33 -0500'
  date_gmt: '2014-08-03 15:01:33 -0500'
  content: "There is another way, but this is less safe than the method above.\r\n\r\n
    \   sudo setpci -s 00:02.0 f4.b=20\r\n\r\nWhere where 20 is the brightness percentage.\r\n\r\nThis
    worked on my HP netbook, but does not work on my Acer.\r\n\r\nhttp://askubuntu.com/questions/195011/how-do-i-adjust-the-screen-brightness-on-an-acer-aspire-one-d270"
---
The latest version of Ubuntu with long term support (LTS) 14.04 came out in April and users are starting to report minor problems. One of the issues is the problem of adjusting screen brightness on notebook computers. In this article, we report a solution for this problem.

## Cause

This issue causes the screen to display blinding maximum luminance and controls have no effect. This is caused by bugs in this version of Ubuntu for Intel and nVidia video cards (see <a href="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1255428" target="_blank">here</a>).

## Solution

This method fixes this issues for Intel integrated graphics, which is what is used in most of notebooks.

1\. Create `/usr/share/X11/xorg.conf.d/20-intel.conf`

2\. Edit and put the following into the `20-intel.conf`:

```
Section "Device"
    Identifier "card0"
    Driver     "intel"
    Option     "Backlight"  "intel_backlight"
    BusID      "PCI:0:2:0"
EndSection
```

3\. Save the file, log out, and log back in. The brightness controls should be working now.