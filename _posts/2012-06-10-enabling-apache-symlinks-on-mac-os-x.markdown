---
layout: post
status: publish
published: true
title: Enabling Apache SymLinks on Mac OS X
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 324
wordpress_url: http://codenuggets.com/?p=324
date: '2012-06-10 17:03:09 -0500'
date_gmt: '2012-06-10 17:03:09 -0500'
categories:
- Programming
- PHP
- Projects
- Dislike
tags:
- PHP
- Mac OS X
- Apache
- symbolic link
- soft link
- FollowSymLinks
- file backup
comments: []
---
Recently my two-and-half year old MacBook Pro has been a little unstable with a few crashes where I had to hard reset to reboot the computer. I have Windows 7 installed using Bootcamp on one partition and sometimes I play I/O intensive games on this computer and I'm not surprised that the crashes are caused by wear and tear of the hard drive due to age.

I have been considering reinstalling the OS's on this computer, but I have to save my projects on this computer before I do that. Most of my files are saved on <a href="http://db.tt/A4X1Ym57" target="_blank">Dropbox</a> during my work days, but there are a couple of PHP website projects located in my Sites folder and these projects can be reached through `http://localhost/~jeff/project/`

What I would like to do is to move these projects to my Dropbox folder, but still allow Apache to serve these projects. I decided to put a link in my Sites folder for each of my projects located in Dropbox so that I can use the same URL. The following are the steps to enable Apache links:

1\. Create the symbolic link to the project folder

```
cd /Users/Jeff/Sites
ln -s /Users/Jeff/Dropbox/Projects/project_name project_name
```

2\. Open the Apache config file for your user name (for me it is `/etc/Apache2/users/Jeff.conf`) and add `FollowSymLinks` to the file so the file is as follows:

```
<Directory "/Users/Jeff/Sites/">
    Options Indexes MultiViews **FollowSymLinks**
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
```

3\. Open the main Apache config file (`/etc/Apache2/httpd.conf`) and add the following line somewhere in there

```
Include /private/etc/apache2/users/*.conf
```

4\. According to <a href="https://discussions.apple.com/thread/1771399?threadID=1771399" target="_blank">this</a>, all levels of the physical path to projects needs to have `read` and `execute` permission. So I did the following:

```
cd /Users/Jeff
chmod a+rx Dropbox
```

5\. Restart Apache

```
sudo /usr/sbin/apachectl restart
```

The projects can be accessed `http://localhost/~jeff/project/`, but not sure why `http://localhost/~jeff/project` does not work.

References:

1. <a href="https://discussions.apple.com/thread/1771399?threadID=1771399" target="_blank">Serving apache files from alternate directories with symbolic links</a>
2. <a href="http://mcapewell.wordpress.com/2006/09/22/restart-apache-in-mac-os-x/" target="_blank">Restart Apache in Mac OS X</a>
