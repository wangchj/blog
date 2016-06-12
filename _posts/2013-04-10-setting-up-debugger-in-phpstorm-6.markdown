---
layout: post
status: publish
published: true
title: Setting up debugger in PHPStorm 6
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 459
wordpress_url: http://codenuggets.com/?p=459
date: '2013-04-10 03:45:48 -0500'
date_gmt: '2013-04-10 03:45:48 -0500'
categories:
- Uncategorized
tags: []
comments:
- id: 2043
  author: Xdebug and phpstorm. | Codeperl's Knowledge Sharing System
  author_email: ''
  author_url: http://codeperl.wordpress.com/2013/05/19/xdebug-and-phpstorm/
  date: '2013-05-19 20:01:25 -0500'
  date_gmt: '2013-05-19 20:01:25 -0500'
  content: "[...] http://codenuggets.com/2013/04/10/setting-up-debugger-in-phpstorm-6/
    [...]"
- id: 2207
  author: Lance
  author_email: lance.caraccioli@gmail.com
  author_url: ''
  date: '2013-07-08 22:19:31 -0500'
  date_gmt: '2013-07-08 22:19:31 -0500'
  content: It seems like this configuration assumes a local install of php.  However
    I have a remote development server I deploy to which is where php and xdebug are
    installed.  How do you setup that type of development environment?
- id: 2213
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2013-07-13 04:45:13 -0500'
  date_gmt: '2013-07-13 04:45:13 -0500'
  content: Hello yes this post does assume local installation of PHP. I was mostly
    concerned about setting up my local dev environment for my project and without
    having to do debugging once the code has moved to a remote server. I'd be interested
    to know how to debugging on remote server. I'm assuming you need to configure
    xdebug on the remote server somehow.
---
This post summarizes the steps to setup debugging using Xdebug for PHP in PHPStorm 6 (one of the best PHP IDE). This post is a more comprehensive version of <a href="http://codenuggets.com/2013/03/01/xdebug-on-ubuntu-10-04/">this previous post</a>.

This post is for Linux environment

**1. Install Xdebug**

Xdebug can be installed from the PECL repository, which is part of PEAR. PECL required php5-dev package. Use the following commands to install these prerequisites:

```
sudo apt-get install php5-dev
sudo apt-get install php-pear
```

Afterwards, Xdebug can be installed via PECL:

```
sudo pecl install xdebug
```

When installation is done, PECL will output where Xdebug is installed as follows:

```
Build process completed successfully
Installing '/usr/lib/php5/20090626/xdebug.so'
install ok: channel://pecl.php.net/xdebug-2.2.1
configuration option "php_ini" is not set to php.ini location
You should add "extension=xdebug.so" to php.ini
```

Modify your php.ini accordingly. My php.ini is located at `/etc/php5/apache2/php.ini`. I added the following lines to the end of my php.ini.

```
zend_extension=/usr/lib/php5/20090626/xdebug.so
[xdebug]
xdebug.remote_enable=on
xdebug.remote_handler=dbgp
xdebug.remote_port=9000
```

Restart Apache

**2. Modify PHPStorm Settings**

Go into Files -> Settings -> Click on PHP. Select an interpreter. The screen should look like follows.

<a href="http://codenuggets.com/wp-content/uploads/2013/04/PHPStorm6-PHP-Settings.png"><img src="http://codenuggets.com/wp-content/uploads/2013/04/PHPStorm6-PHP-Settings-1024x527.png" alt="PHPStorm6-PHP-Settings" width="550" height="283" class="alignnone size-large wp-image-462" /></a>

Click on '...' for Interpreter. The Interpreters window shows up (see below). Click on the green +, and an interpreter. Choose Xdebug for debugger and click OK.

<a href="http://codenuggets.com/wp-content/uploads/2013/04/PHPStorm6-Add-Interpreter.png"><img src="http://codenuggets.com/wp-content/uploads/2013/04/PHPStorm6-Add-Interpreter.png" alt="PHPStorm6 Add Interpreter" width="550" class="alignnone" /></a>

Click on Debug in the Settings Window. The settings should match what you get back from installing Xdebug.

<a href="http://codenuggets.com/wp-content/uploads/2013/04/PHPStorm-PHP-Debug-Settings.png"><img src="http://codenuggets.com/wp-content/uploads/2013/04/PHPStorm-PHP-Debug-Settings.png" alt="PHPStorm-PHP-Debug-Settings" width="550" class="alignnone size-large wp-image-463" /></a>

Click on Apply button and OK.

**3. Debug Configuration**

Go into Run -> Edit Configurations.

<a href="http://codenuggets.com/wp-content/uploads/2013/04/Screenshot-Run-Debug-Configurations.png"><img src="http://codenuggets.com/wp-content/uploads/2013/04/Screenshot-Run-Debug-Configurations.png" alt="Screenshot-Run-Debug Configurations" width="550" class="alignnone" /></a>

Click on the "green plus" and select PHP Web Application

Next to Server, click on the "..." button and servers settings shows up. Click on the green plus to add a server setting. Use the following settings:

- Name: can be anything
- Host: localhost
- Port: 80
- Debugger: Xdebug

<a href="http://codenuggets.com/wp-content/uploads/2013/04/Screenshot-PHPStorm-Servers.png"><img src="http://codenuggets.com/wp-content/uploads/2013/04/Screenshot-PHPStorm-Servers.png" alt="Screenshot-PHPStorm-Servers" width="550" class="alignnone" /></a>

Click on OK

Back in the Run/Debug Configurations window, change the Start URL to the URL of your application (see figure above), and click OK.