---
layout: post
status: publish
published: true
title: XDebug on Ubuntu 10.04
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 421
wordpress_url: http://codenuggets.com/?p=421
date: '2013-03-01 02:02:21 -0600'
date_gmt: '2013-03-01 02:02:21 -0600'
categories:
- Programming
- PHP
- MDPX Interface
tags:
- Linux
- PHP
- Eclipse
- Debugger
- Ubuntu
- Xdebug
comments:
- id: 1967
  author: Setting up debugger in PHPStorm 6 « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2013/04/10/setting-up-debugger-in-phpstorm-6/
  date: '2013-04-11 04:49:18 -0500'
  date_gmt: '2013-04-11 04:49:18 -0500'
  content: "[...] This post summarizes the steps to setup debugging using Xdebug for
    PHP in PHPStorm 6 (one of the best PHP IDE). This post is a more comprehensive
    version of this previous post. [...]"
---
In the <a href="http://codenuggets.com/2012/06/04/setting-up-xdebug-for-eclipse-pdt-on-mac-os-x/" target="_blank">previous post</a>, I noted how to setup XDebug on MacOSX. My MacBook is broken, and I switching my PHP development to my Ubuntu environment. I have to admit, my Ubuntu system is a bit old runing 10.04 LTS.

I followed <a href="http://www.rdeeson.com/weblog/102/installing-xdebug-for-use-with-eclipse-on-ubuntu-linux.html">http://www.rdeeson.com/weblog/102/installing-xdebug-for-use-with-eclipse-on-ubuntu-linux.html</a> to install Xdebug.

After running `sudo pecl install xdebug`, this is the result I received:

<blockquote>
Build process completed successfully<br />
Installing '/usr/lib/php5/20090626/xdebug.so'<br />
install ok: channel://pecl.php.net/xdebug-2.2.1<br />
configuration option "php_ini" is not set to php.ini location<br />
You should add "extension=xdebug.so" to php.ini

</blockquote>
The location of my php.ini is `/etc/php5/apache2/php.ini`

Restart Apache

