---
layout: post
status: publish
published: true
title: LAMP Development Environment Setup
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 480
wordpress_url: http://codenuggets.com/?p=480
date: '2013-04-26 04:37:45 -0500'
date_gmt: '2013-04-26 04:37:45 -0500'
categories:
- PHP
tags:
- Linux
- PHP
- Ubuntu
- Apache
- MySQL
comments: []
---
LAMP stands for Linux, Apache, MySQL and PHP. This article summarizes how to install and configure Apache2, PHP 5, MySQL on Ubuntu 13.04

**Install Apache 2**

```
sudo apt-get install apache2
```

**Install PHP**

```
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```
**Enable User Document Directory**

```
# Create User Directory
mkdir ~/public_html

# Enable User Dir
cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/userdir.load
sudo ln -s ../mods-available/userdir.conf

# Restart Apache
sudo /etc/init.d/apache2 restart
```

http://heriman.wordpress.com/2008/08/05/enabling-apache-user-home-public_html-directory-in-ubuntu/  
http://httpd.apache.org/docs/2.2/howto/public_html.html

**Enable PHP in User Directory**

Open `/etc/apache2/mods-enabled/php5.conf` in an editor. Comment out the section that says "Running PHP scripts in user directories..."

Restart Apache

**Install MySQL**

```
sudo apt-get install mysql-server
```

The setup should ask to set root password/

If you are running PHP you will also need to install the php module for mysql 5:

```
sudo apt-get install php5-mysql
```

<a href="http://www.howtogeek.com/howto/ubuntu/install-mysql-server-5-on-ubuntu/">Install MySQL Server 5 on Ubuntu</a>

**Remove MySQL Anonymous User**

> By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them.  This is intended only for testing, and to make the installation go a bit smoother.  You should remove them before moving into a production environment.


```
sudo mysql_secure_installation
```

<a href="http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-introducing-mysql-server/">Ubuntu 12.04 LTS Precise Pangolin: Introducing MySQL Server</a>

**Enable Remote Access**

1. Open `/etc/mysql/my.cnf` in an editor.
2. Comment out the line `bind-address = 127.0.0.1`
3. Restart MySQL
