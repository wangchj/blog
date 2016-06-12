---
layout: post
status: publish
published: true
title: Installing ASP.NET on Ubuntu with Mono
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 150
wordpress_url: http://codenuggets.com/?p=150
date: '2011-01-14 11:02:58 -0600'
date_gmt: '2011-01-14 11:02:58 -0600'
categories:
- Programming
- ASP.NET
- ".NET"
tags:
- Linux
- Ubuntu
- Mono
comments:
- id: 661
  author: Installing ASP.NET on Ubuntu with Mod_Mono Autoconfig « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/05/23/installing-asp-net-on-ubuntu-with-mod_mono-autoconfig/
  date: '2012-05-23 19:06:20 -0500'
  date_gmt: '2012-05-23 19:06:20 -0500'
  content: "[...] the previous post, Installing ASP.NET on Ubuntu with Mono, I outlined
    the step of enabling ASP.NET application on Apache using mod_mono without autoconfig.
    [...]"
---
Note: an updated post can be found <a href="http://codenuggets.com/2012/05/23/installing-asp-net-on-ubuntu-with-mod_mono-autoconfig/">here</a>.

Most of people would think that ASP.NET would only run on Windows with IIS. After all most of products of Microsoft are proprietary. With the Mono Project, the entire .NET infrastructure, including C# compiler and ASP.NET, has been ported and is now possible to run on Linux (among other) environments. These are the steps I took to configure the environment.

## 1. Install Mono

The first step is to install Mono on the Linux machine. Fortunately for me, Mono is a core service on Ubuntu 10.10 so it is installed by default. The reason it's a core service is that there are some applications included in the distribution depend on the .NET Framework of Mono. For other Linux distributions, installation might be required.

The Mono installation includes .NET Framework 2.0 (partial 3.0 and 4.0), C# compiler, and .NET Runtime.

__Note__ (3-31-2012): For later version of Ubuntu that doesn't have Mono pre-installed, the following commands Mono Runtime and gmcs C# compiler:

```
sudo apt-get install mono-runtime
sudo apt-get install mono-gmcs
```

## 2. Install Apache

In Ubuntu, the command to install apache is

```
sudo apt-get install apache2
```
  
## 3. Install Apache ASP.NET module (Mod_Mono)

The following are the steps to install and configure

```
sudo apt-get install libapache2-mod-mono
sudo apt-get install mono-apache-server2
sudo a2enmod mod_mono
```

Complete instructions are https://help.ubuntu.com/community/ModMono

## 4. Edit Apache config to activate Mod_Mono

__Note__ (5-22-2012): This step is no longer needed since newer version will add an Apache configuration file called "mod_mono.load", in the "mods-enabled" folder, which contains the following LoadModule line.

I don't remember the exact steps, but I remember it's only a one line change. Basically the following line should be somewhere in the Apache config file

```
LoadModule mono_module /usr/lib/httpd/modules/mod_mono.so
```

## 5. Enable AutoConfiguration
This make deployment of ASP.NET applications easier so that all you have to do is copy the application files to a folder and it should work.
The steps are http://www.mono-project.com/AutoHosting

## 6. Additional Notes

In addition, I created an alias in the Apache config file to point to the www folder in my home directory so that http://localhost/jeff/ will point to my www directory.

I'm still testing how well ASP.NET Mono works. After a few small apps, I don't see a lot of problem, except when I first installed, when ASP.NET encounter an exception, the server would not refresh the app, even after I corrected the exception. The problem seems to resolved itself, since I no longer have that problem. Also thein web.config does not take the value of "Windows". I will see as I develop more complex applications.