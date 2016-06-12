---
layout: post
status: publish
published: true
title: Setting Up PHP Development Environment Using Eclipse PDT and Zend Server CE
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 20
wordpress_url: http://codenuggets.com/?p=20
date: '2012-02-16 04:11:49 -0600'
date_gmt: '2012-02-16 04:11:49 -0600'
categories:
- Programming
- PHP
tags:
- PHP
- Zend
- Eclipse
- Debugger
- Yii
comments:
- id: 7
  author: Victor Marques
  author_email: victor.cattechnologies@gmail.com
  author_url: http://www.cattechnologies.com/offshorePHPDevelopment.aspx
  date: '2012-03-05 09:58:09 -0600'
  date_gmt: '2012-03-05 09:58:09 -0600'
  content: Nice information about PHP development.
- id: 56
  author: Darrel Weavers
  author_email: Cerni971@gmail.com
  author_url: http://www.adddnpvy.com
  date: '2012-04-05 03:58:42 -0500'
  date_gmt: '2012-04-05 03:58:42 -0500'
  content: I like this post, enjoyed this one  appreciate it for  putting up.
- id: 79
  author: David Cassiday
  author_email: 4Crosson@yahoo.com
  author_url: http://wannabeolympics.com/story.php?id=74893
  date: '2012-04-07 21:37:29 -0500'
  date_gmt: '2012-04-07 21:37:29 -0500'
  content: But wanna remark on few general things, The website design and style is
    perfect, the content is really superb. "Drop the question what tomorrow may bring,
    and count as profit every day that fate allows you." by Horace.
- id: 87
  author: backlink building tips
  author_email: Kuban9276@gmail.com
  author_url: http://www.glbsocial.net/blog.php?user=bradharding1024&blogentry_id=86314
  date: '2012-04-08 01:31:02 -0500'
  date_gmt: '2012-04-08 01:31:02 -0500'
  content: Hello can you mind permitting me realize that webhost you're making use
    of? I've loaded your internet site in 3 completely different browsers and I need
    to say this website a lot much faster then nearly all. Can an individual suggest
    a good web hosting provider with a honest value? Kudos, I enjoy it!
- id: 669
  author: Setting up Xdebug for Eclipse PDT on Mac OS X « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2012/06/04/setting-up-xdebug-for-eclipse-pdt-on-mac-os-x/
  date: '2012-06-04 05:57:07 -0500'
  date_gmt: '2012-06-04 05:57:07 -0500'
  content: "[...] the previous post, I outline the steps to configure Zend Debugger
    debugging PHP application in Eclipse PDT. [...]"
- id: 5010
  author: clash of clans hack tool 2015,clash of clans hack download apk,clash of
    clans hack activation code,clash of clans hack cydia july 2015,clash of clans
    hack apk 2015,clash of clans hack download apk android,clash of clans hack no
    survey,clash of clans hack
  author_email: jeanettfulford@gmail.com
  author_url: http://clashofclanshackjack.blogspot.com/
  date: '2015-10-20 16:18:13 -0500'
  date_gmt: '2015-10-20 16:18:13 -0500'
  content: COC on-line generator is a technique that doesn't require obtain and works
    very quickly.
- id: 5023
  author: Stas Ustimenko
  author_email: stas@codelobster.com
  author_url: http://www.codelobster.com
  date: '2015-10-23 07:06:37 -0500'
  date_gmt: '2015-10-23 07:06:37 -0500'
  content: 'I prefer to use Codelobster instead of Eclipse: http://www.codelobster.com'
---
I'm setting up a PHP development environment on my Mac. I'd like to develop some web applications using the <a href="http://www.yiiframework.com/">Yii Framework</a>. I'm fairly new to PHP development. I'm looking for an environment that allow me to edit and debug my PHP scripts.

<span style="text-decoration: underline;">Zend Server CE Installation</span>

I installed the development environment offered by Zend and found it to be one of the easiest environment to set up. The components are downloaded from <a href="http://www.zend.com/en/community/pdt">http://www.zend.com/en/community/pdt</a>. The following are the steps I took to install the environment:

1. Download and install Eclipse PDT All-in-One
2. Download and install Zend Server CE

After the steps I was able to debug PHP scripts.

It's useful to add the two directories to path (to access mysql, for example):

- `usr/local/zend/bin`
- `/usr/local/zend/mysql/bin`

<span style="text-decoration: underline;">MySQL Setup</span>

By default MySQL does not accept TCP/IP connection (only UNIX socket connections). To enable TCP/IP connection, comment out the line `skip-networking` from `my.cnf` (see below for the location of file).

<span style="text-decoration: underline;">Installation Details</span>

Everything is installed at /usr/local/zend/.

Installed components follows:

- PHP
    - Executable: /usr/local/zend/bin/
    - php.ini: /usr/local/zend/etc/php.ini
- Apache
    - Document root: /usr/local/zend/apache2/htdocs/
    - Root URL: <a href="http://localhost:10088/">http://localhost:10088/</a>

- MySQL
    - my.cnf: /usr/local/zend/mysql/data/my.cnf
    - Initially root has no password
    - To start: sudo zendctl.sh start-mysql
- phpMyAdmin
    - URL: <a href="https://localhost:10082/phpmyadmin/">https://localhost:10082/phpmyadmin/</a>
- Zend Debugger
- Zend Server
    - Admin page: <a href="https://localhost:10082/">https://localhost:10082/</a> or <a href="http://localhost:10081/">http://localhost:10081/</a>