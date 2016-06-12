---
layout: post
status: publish
published: true
title: Count Digits in an Integer
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1489
wordpress_url: http://codenuggets.com/?p=1489
date: '2015-03-20 16:36:17 -0500'
date_gmt: '2015-03-20 16:36:17 -0500'
categories:
- Programming
- Java
tags:
- Java
- Java Tip
- Java Algorithm
comments: []
---
The following snippet uses `log()` to find the number of digits in the integer `x`. The result is 5.

{% highlight java %}
int x = 12345;
int length = (int)(Math.log10(x) + 1);
{% endhighlight %}

Source: [http://stackoverflow.com/questions/1306727/way-to-get-number-of-digits-in-an-int](http://stackoverflow.com/questions/1306727/way-to-get-number-of-digits-in-an-int)

