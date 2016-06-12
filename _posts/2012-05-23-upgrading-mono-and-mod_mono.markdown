---
layout: post
status: publish
published: true
title: Upgrading Mono and Mod_Mono
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 280
wordpress_url: http://codenuggets.com/?p=280
date: '2012-05-23 21:17:10 -0500'
date_gmt: '2012-05-23 21:17:10 -0500'
categories:
- School
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ASP.NET
- ".NET"
tags:
- Linux
- ASP.NET
- Ubuntu
- Mono
- Apache
- mod_mono
- mod_mono autoconfig
comments: []
---
I've been trying to run one of my research ASP.NET application on Ubuntu. I kept getting an error some very obscure error message that says <code>"Warning **: Missing method .ctor [..]"</code> (for the entire message see <a href="http://codenuggets.com/2012/05/23/asp-net-mono-missing-method-ctr-in-assembly/">this post</a>. After long research on the web, I found that my mono installation is out of date and my application is written in .NET Framework 4.

To support newer version of .NET Framework, I have to update my Mono from version 2.6 to 2.10 which is only provided by <a href="http://badgerports.org/">BadgerPorts</a>. See my previous post <a href="http://codenuggets.com/2012/03/26/install-monodevelop-on-ubuntu/">"Install MonoDevelop on Ubuntu"</a> to configure Ubuntu software source to use BadgerPorts.

Once BadgerPorts has been added as a software source, do the following step:


1. Go into **System**-> **Administration** -> **Synaptic Package Manager**
2. Search for mono
3. For each package mentioned <a href="http://codenuggets.com/2012/05/23/installing-asp-net-on-ubuntu-with-mod_mono-autoconfig/">here</a>, click on the check box next to Package name and select "Mark for upgrade"

Restart Apache.