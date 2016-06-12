---
layout: post
status: publish
published: true
title: PHP Objects Passed By Reference
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 565
wordpress_url: http://codenuggets.com/?p=565
date: '2013-09-23 03:38:54 -0500'
date_gmt: '2013-09-23 03:38:54 -0500'
categories:
- Programming
- PHP
tags:
- PHP 5
- objects
- pass by reference
comments: []
---
In a <a href="http://codenuggets.com/2013/03/04/php-array-passed-by-value/" target="_blank">previous</a> post, I mentioned that arrays in PHP are passed by value.ce,

For some reason, there are mixed information about if PHP objects are passed by reference, so I decided to write a short block of code to find out. The result is, as PHP 5, <em>object are passed by reference</em>.

The following is a short PHP file for the purpose of testing.

{% highlight php %}
<?php
class Test
{
    public $a = 'abc';
    public $b = 'cde';
}

function change($test)
{
    $test->a = 'aaa';
    $test->b = 'bbb';
}

$test = new Test;
echo "Before: a = $test->a, b = $test->b <br/>";
change($test);
echo "After: a = $test->a, b = $test->b";
?>
{% endhighlight %}

The output of this PHP file from the web server follows:

```
Before: a = abc, b = cde
After: a = aaa, b = bbb
```

This shows, PHP passes objects by reference.

Reference: http://stackoverflow.com/questions/2715026/are-php5-objects-passed-by-reference

