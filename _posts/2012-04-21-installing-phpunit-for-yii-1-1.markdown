---
layout: post
status: publish
published: true
title: Installing PHPUnit for Yii 1.1
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 205
wordpress_url: http://codenuggets.com/?p=205
date: '2012-04-21 06:47:38 -0500'
date_gmt: '2012-04-21 06:47:38 -0500'
categories:
- Uncategorized
- Programming
- PHP
- Projects
- Dislike
tags:
- Yii
- PHPUnit
- unit testing
- Selenium
- functional testing
comments:
- id: 601
  author: Ray Stoeckicht
  author_email: raysto@zurmo.com
  author_url: http://zurmo.org
  date: '2012-04-30 18:59:44 -0500'
  date_gmt: '2012-04-30 18:59:44 -0500'
  content: "Nice tutorial on Yii. It is great to see someone publishing quality content
    on the framework. We have been working on an open source CRM application that
    is written in PHP utilizing JQuery, Yii, and RedBeanPHP and relies heavily on
    test driven development. \r\n\r\nZurmo might be one of the most complex projects
    on Yii to date. Right now, we have 1000+ unit tests running across eight server
    configurations. We utilize selenium as well for a nice set of functional tests
    too. It would be incredibly helpful to get your technical feedback and recommendations
    so that we can improve the application. Take a look and let me know what you think:
    http://zurmo.org"
- id: 798
  author: Deepak
  author_email: thong.deep@gmail.com
  author_url: ''
  date: '2012-08-02 19:10:31 -0500'
  date_gmt: '2012-08-02 19:10:31 -0500'
  content: Thank you very. I was fully frustrated with this selenium issue but finally
    got the problem solved.
- id: 2151
  author: PHPUnit for Yii 1.1 &#8211; Update « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2013/06/27/phpunit-for-yii-1-1-update/
  date: '2013-06-27 02:04:22 -0500'
  date_gmt: '2013-06-27 02:04:22 -0500'
  content: "[...] which uses Yii 1.1 Framework. I have already written about installing
    PHPUnit for Yii 1.1 in another post. Today followed the steps in the previous
    post. PHPUnit installed fine, but there it gives me [...]"
- id: 2758
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2014-03-13 06:03:47 -0500'
  date_gmt: '2014-03-13 06:03:47 -0500'
  content: Thanks for the comment. I'm glad this post is helpful!
- id: 4344
  author: Nichol
  author_email: lylesommer@web.de
  author_url: http://Young.de
  date: '2015-03-07 18:00:38 -0600'
  date_gmt: '2015-03-07 18:00:38 -0600'
  content: "Hi admin, i found this post on 13 spot in google's search results.\r\nI'm
    sure that your low rankings are caused by hi bounce rate.\r\nThis is very important
    ranking factor. One of the biggest reason for high bounce rate is due to visitors
    hitting the back button. The \r\nhigher your bounce rate the further down the
    search results your \r\nposts and pages will end up, so having reasonably low
    bounce \r\nrate is important for improving your rankings naturally.\r\nThere is
    very handy wordpress plugin which can help you. Just search in google for:\r\n\r\nSeyiny's
    Bounce Plugin"
---
## Intro

Yii Framwork utilizes the PHPUnit for unit testing and quality assurance. I'm setting up the development environment using Yii for a web application project and following its development methodology.

Yii utilizes the core PHPUnit unit testing functionality and the Selenium extension. PHPUnit is solely for unit testing and I believe Selenium is a functional testing tool/framework for web application (I yet to try). I'm using Mac OS X Snow Leopard.

## Install PHPUnit

The following commands are taken from the <a href="http://www.phpunit.de/manual/3.6/en/installation.html">PHPUnit documentation</a>.

```
sudo pear config-set auto_discover 1
sudo pear install pear.phpunit.de/PHPUnit
```

I believe this is enough just to do unit testing. The following two code segments shows a simple test case of project/src/Operations.php and projects/tests/OperationsTest.php:

{% highlight php %}
<?php

/* Operations.php */

class Operations
{
	public static function double($x)
	{
		return $x * 2;
	}
}
?>
{% endhighlight %}

{% highlight php %}
<?php

/* OperationTest.php */

require_once("../src/Operations.php");

class OperationsTest extends PHPUnit_Framework_TestCase
{
	function testDouble()
	{
		$this->assertEquals(2, Operations::double(1));
	}
}
?>
{% endhighlight %}

## Installing Selenium PHPUnit Extension

Testing Framework of Yii references some Selenium extension classes I get erros running Yii test cases with installing Selenium; therefore, I'm certain the extension is required to use Yii's testing  framework. The following command installs the extension:

```
sudo pear install phpunit/PHPUnit_Selenium
```

## Composing and Running Unit Tests via Yii

The following is a sample class and a sample test class for the class. The class is a very simple Yii controller class and is located at `app/protected/controllers/MessageTest.php`, and the test is located at `app/protected/tests/unit/MessageTest.php`.

<u>MessageController.php:</u>

{% highlight php %}
<?php

class MessageController extends Controller
{
	public function repeat($msg)
	{
		return $msg;
	}
}
?>
{% endhighlight %}

<u>MessageTest.php:</u>

{% highlight php %}
<?php
Yii::import('application.controllers.MessageController');

class MessageTest extends CTestCase
{
	public function testRepeat()
	{
		$contr = new MessageController('messageTest');
		$msg = 'Hello, anyone out there?';
		$this->assertEquals($msg, $contr->repeat($msg));
	}
}
?>
{% endhighlight %}

The following commands run this simple unit test.

```
cd app/protected/tests
phpunit unit/MessageTest.php
```