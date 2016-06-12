---
layout: post
status: publish
published: true
title: Least Significant Digits of Integer
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1485
wordpress_url: http://codenuggets.com/?p=1485
date: '2015-03-19 18:00:23 -0500'
date_gmt: '2015-03-19 18:00:23 -0500'
categories:
- Programming
- Java
tags:
- algorithm
- least significant digit
- Java Tip
- Java Algorithm
- modulo operator
- modulo
comments: []
---
Least significant digits of an integer can be obtained by performing modulo of power of 10. Note that modulo is the division remainder operator.

The following shows examples of obtaining least significant digits.

{% highlight java %}
int x = 1234;
int d = 0;

d = x % 10;   //Get the first digit  d = 4
d = x % 100;  //Get the second digit d = 34
d = x % 1000; //Get the third digit  d = 234
{% endhighlight %}

The following simple method can be used to find the first `k` of `x`.

{% highlight java %}
public int firstDigits(x, k) {
    int[] p = {1, 10, 100, 1000, 10000, 100000, 100000};

    if(k == 0)
        throw new IllegalArgumentException("Modulo by 0");

    return x % p[k];
}
{% endhighlight %}