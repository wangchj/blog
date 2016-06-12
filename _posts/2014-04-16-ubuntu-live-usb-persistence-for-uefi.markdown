---
layout: post
status: publish
published: true
title: Ubuntu Live USB Persistence For UEFI
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 651
wordpress_url: http://codenuggets.com/?p=651
date: '2014-04-16 06:08:22 -0500'
date_gmt: '2014-04-16 06:08:22 -0500'
categories:
- OS
- Ubuntu
tags:
- Linux
- Ubuntu
- Ubuntu 13.10
- UEFI
- EFI
- Ubuntu Live USB
- persistent
comments:
- id: 3408
  author: Danilo
  author_email: adrienewillis@live.de
  author_url: http://Gale.wikispaces.com
  date: '2014-08-24 21:54:36 -0500'
  date_gmt: '2014-08-24 21:54:36 -0500'
  content: "I read a lot of interesting posts here. Probably you  spend \r\na lot
    of time writing, i know how to save you a lot of work, there is an online tool
    that creates unique, google friendly articles in seconds,\r\njust type in google
    \ - laranitas free content source"
- id: 3421
  author: find out this here
  author_email: percyjardine@freenet.de
  author_url: https://www.facebook.com/william.holly.7
  date: '2014-08-27 04:53:07 -0500'
  date_gmt: '2014-08-27 04:53:07 -0500'
  content: "My partner and I stumbled over here by a different web address and thought
    I may as well check \r\nthings out. I like what I see so i am just following you.\r\n\r\nLook
    forward to finding out about your web page again.\r\n\r\nHave a look at my page
    - <a href=\"https://www.facebook.com/william.holly.7\" rel=\"nofollow\">find out
    this here</a>"
- id: 3449
  author: what should i sell online
  author_email: sheliareid@web.de
  author_url: http://youtu.be/xfdMrE9uL3E
  date: '2014-09-01 23:51:21 -0500'
  date_gmt: '2014-09-01 23:51:21 -0500'
  content: "Greetings from Idaho! I'm bored at work so I decided to browse your blog
    on my iphone during lunch \r\nbreak. I enjoy the information you provide here
    and can't \r\nwait to take a look when I get home. I'm shocked at how quick your
    blog loaded \r\non my cell phone .. I'm not even using WIFI, just \r\n3G .. Anyhow,
    great blog!"
- id: 3486
  author: prostate massage
  author_email: jerrodfernando@yahoo.de
  author_url: http://www.dailymotion.com/video/x1w2xpl_why-men-love-prostate-milking-watch-controversial-video_news
  date: '2014-09-07 20:12:03 -0500'
  date_gmt: '2014-09-07 20:12:03 -0500'
  content: "I was curious if you ever thought of changing the layout of your website?\r\n\r\nIts
    very well written; I love what youve got to say.\r\nBut maybe you could a little
    more in the way of content so \r\npeople could connect with it better. Youve got
    an awful lot of text \r\nfor only having 1 or two pictures. Maybe you \r\ncould
    space it out better?"
- id: 4628
  author: Rob
  author_email: n4rps@yahoo.com
  author_url: http://www.04c.org
  date: '2015-06-10 13:02:26 -0500'
  date_gmt: '2015-06-10 13:02:26 -0500'
  content: Nice tutorial for making the UEFI LiveUSB persistent! If you'd consider
    also adding how to create a UEFI LiveUSB using unetbootin, you'd then have a nice
    'one-stop shopping' tutorial for creating a persistent UEFI Live USB!
- id: 4629
  author: Rob
  author_email: n4rps@yahoo.com
  author_url: http://www.04c.org
  date: '2015-06-10 13:06:18 -0500'
  date_gmt: '2015-06-10 13:06:18 -0500'
  content: "Nice tutorial for making the UEFI LiveUSB persistent! If you'd consider
    also adding how to create a UEFI LiveUSB using unetbootin, you'd then have a nice
    'one-stop shopping' tutorial for creating a persistent UEFI Live USB!\r\n\r\nhttp://askubuntu.com/questions/138356/how-do-i-get-a-live-usb-to-use-a-partition-for-persistence"
---
What is nice about recent Ubuntu distribution is that you can create a bootable USB drive from the downloaded image and run Ubuntu directly from the USB drive without installing it (Live USB). When you're creating the bootable drive, you often have the choice of data persistence across live session. Without persistence option enable, the files create and packages installed on the file system / will be lost next time you boot into the system using the USB drive. With persistence, these settings will be saved.

Recently I've created a bootable drive with persistence enable, but found that my files and packages are lost after reboots. After some research, I found that this is a bug in Ubuntu Live USB creator that for newer computer with UEFI (or EFI). See references below for details of the bug.

Digging deeper I found that for non-UEFI the OS is initialized with `syslinux.cfg`, persistence is enabled as follows:

```
...

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- persistent

...
```

For UEFI computers, the system is initialized with Grub, but persistence flag is not set in `/boot/grub/grub.cfg`. What worked for me is to add the persistence flag to the line that starts with `linux` as follows:

```
...
menuentry "Try Ubuntu without installing" {
        set gfxpayload=keep
        linux   /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
        initrd  /casper/initrd.lz
}
...
```

Although I was able to persist my settings, I was a bit disappointed with the performance of the system after the setting is enabled. I think I'll explore other alternatives of portable Linux with better performance.

The version of Ubuntu is 13.10 64-bit version.

References:

1. <a href="http://ubuntuforums.org/showthread.php?t=2186074">[SOLVED] how to fix bug 1159016 (can't make 13.10 Live USB persistent)</a>
2. <a href="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1159016">64 bit live-USB successfully boots, but without persistence on UEFI pc</a>
3. <a href="http://askubuntu.com/questions/291732/persistent-file-not-working-for-13-04">Persistent file NOT working for 13.04</a>