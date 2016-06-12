---
layout: post
status: publish
published: true
title: Installing ASP.NET on Ubuntu with Mod_Mono Autoconfig
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 261
wordpress_url: http://codenuggets.com/?p=261
date: '2012-05-23 19:06:16 -0500'
date_gmt: '2012-05-23 19:06:16 -0500'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ASP.NET
- ".NET"
tags:
- Linux
- Ubuntu
- Mono
- Apache
- mod_mono
- mod_mono autoconfig
comments:
- id: 662
  author: Installing ASP.NET on Ubuntu with Mono « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2011/01/14/installing-asp-net-on-ubuntu-with-mono/
  date: '2012-05-23 19:13:08 -0500'
  date_gmt: '2012-05-23 19:13:08 -0500'
  content: "[...] Note: an updated post can be found here. [...]"
- id: 901
  author: Jared
  author_email: jaredbroad@gmail.com
  author_url: ''
  date: '2012-08-17 20:35:55 -0500'
  date_gmt: '2012-08-17 20:35:55 -0500'
  content: Thanks worked perfectly.
- id: 4235
  author: danielud
  author_email: danielud@gmail.com
  author_url: ''
  date: '2015-02-01 00:53:58 -0600'
  date_gmt: '2015-02-01 00:53:58 -0600'
  content: "this one... this one is THE ONLY ONE that worked for me. \r\nusing lubuntu.\r\n\r\ni
    was stuck with mod_mono.\r\n\r\nThanks a LOT!"
- id: 4722
  author: linux上部署ASP.NET | MoDoFo.println(&quot;
  author_email: ''
  author_url: http://zhangv.com/wordpress/archives/1845
  date: '2015-07-17 03:05:20 -0500'
  date_gmt: '2015-07-17 03:05:20 -0500'
  content: "[&#8230;] Installing ASP.NET on Ubuntu with Mod_Mono Autoconfig [&#8230;]"
---
In the previous post, <a href="http://codenuggets.com/2011/01/14/installing-asp-net-on-ubuntu-with-mono/">Installing ASP.NET on Ubuntu with Mono</a>, I outlined the step of enabling ASP.NET application on Apache using mod_mono without <a href="http://mono-project.com/AutoHosting">autoconfig</a>. This post provides steps for configuring mod_mono autoconfig targeting ASP.NET 4. This post overlaps and supersedes the previous article.

This post assumes Apache 2 is installed. If this is not the case, see the previous post. The following are Linux shell commands for the process.

## 1. Install Mono

```
sudo apt-get install mono-runtime
sudo apt-get install mono-gmcs
```

## 2. Install mod_mono

```
sudo apt-get install libapache2-mod-mono
sudo apt-get install mono-apache-server2
```

## 3. Enable mod_mono autoconfig

```
sudo a2enmod mod_mono_auto
```

For new installation this is all that's need to enable mod_mono. For older installation with existing Apache configuration files, make sure the following directives somewhere in one of Apache configuration files. For new installation the following are already included in /etc/mono-server4/mono-server4-hosts.conf, which is included in the main configuration file.
    
```
MonoAutoApplication enabled
MonoServerPath default /usr/bin/mod-mono-server4
```

## 4. Restart Apache
   
```
/etc/init.d/apache2 restart
```

**References**

1. <a href="http://mono-project.com/AutoHosting">mod_mono AutoConfiguration</a>
2. <a href="https://help.ubuntu.com/community/ModMono">Ubuntu ModMono</a>
