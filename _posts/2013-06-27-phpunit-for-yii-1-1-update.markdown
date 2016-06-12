---
layout: post
status: publish
published: true
title: PHPUnit for Yii 1.1 - Update
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 536
wordpress_url: http://codenuggets.com/?p=536
date: '2013-06-27 02:04:17 -0500'
date_gmt: '2013-06-27 02:04:17 -0500'
categories:
- Programming
- PHP
tags:
- Linux
- PHP
- Yii
- Ubuntu
- PHPUnit
- unit testing
- Selenium
- Ubuntu 13.04
- Yii 1.1
- PHPUnit 3.7
comments:
- id: 2735
  author: Chris Edwards
  author_email: chris@chrisedwards.ws
  author_url: http://chrisedwards.ws
  date: '2014-01-17 03:11:56 -0600'
  date_gmt: '2014-01-17 03:11:56 -0600'
  content: Thanks!  Worked Perfect!
- id: 2737
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-01-27 21:26:12 -0600'
  date_gmt: '2014-01-27 21:26:12 -0600'
  content: Thanks for the comment!
---
Recently, I have been working on the MDPX project which uses Yii 1.1 Framework. I have already written about installing PHPUnit for Yii 1.1 in <a href="http://codenuggets.com/2012/04/21/installing-phpunit-for-yii-1-1/">another post</a>. Today followed the steps in the previous post. PHPUnit installed fine, but there it gives me errors when I run my unit tests. After some research, I found there are some addition packages I need to install.

The updated commands to install PHPUnit folows. This is done on Ubuntu 13.04, PHPUnit 3.7.21.

```
sudo pear config-set auto_discover 1
sudo pear install pear.phpunit.de/PHPUnit
sudo pear install --alldeps --force phpunit/phpunit
sudo pear install phpunit/DbUnit
sudo pear install phpunit/PHPUnit_Story
```

Yii testing framework requires Selenium. Install with following command

```
sudo pear install phpunit/PHPUnit_Selenium
```

Note: Selenium requires PHP cURL library. If it's not already installed, it can be installed with

```
sudo apt-get install php5-curl
```

The follow are the error messages I received

```
1) UsersTest::testRead
PHP Warning:  include(PHP_Invoker.php): failed to open stream: No such file or directory in /home/wangchj/public_html/yii/framework/YiiBase.php on line 421
PHP Warning:  include(): Failed opening 'PHP_Invoker.php' for inclusion (include_path='.:/home/wangchj/public_html/mdpx/protected/components:/home/wangchj/public_html/mdpx/protected/models:/usr/share/php:/usr/share/pear') in /home/wangchj/public_html/yii/framework/YiiBase.php on line 421
PHP Warning:  include(PHPUnit_Extensions_Database_TestCase.php): failed to open stream: No such file or directory in /home/wangchj/public_html/yii/framework/YiiBase.php on line 421
PHP Warning:  include(): Failed opening 'PHPUnit_Extensions_Database_TestCase.php' for inclusion (include_path='.:/home/wangchj/public_html/mdpx/protected/components:/home/wangchj/public_html/mdpx/protected/models:/usr/share/php:/usr/share/pear') in /home/wangchj/public_html/yii/framework/YiiBase.php on line 421
PHP Warning:  include(PHPUnit_Extensions_Story_TestCase.php): failed to open stream: No such file or directory in /home/wangchj/public_html/yii/framework/YiiBase.php on line 421
```

References<br />
- http://ubuntuforums.org/showthread.php?t=391313<br />
- http://stackoverflow.com/questions/8078707/cannot-get-phpunit-working<br />
- http://www.yiiframework.com/forum/index.php/topic/25744-phpunit-yiibasephp/<br />
- http://stackoverflow.com/questions/13625842/phpunit-extension-warning-in-yii

