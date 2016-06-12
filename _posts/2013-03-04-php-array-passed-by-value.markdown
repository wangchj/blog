---
layout: post
status: publish
published: true
title: PHP Array Passed by Value
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 428
wordpress_url: http://codenuggets.com/?p=428
date: '2013-03-04 02:27:00 -0600'
date_gmt: '2013-03-04 02:27:00 -0600'
categories:
- School
- Programming
- PHP
- Projects
- MDPX Interface
tags:
- PHP
comments:
- id: 2580
  author: PHP Objects Passed By Reference « CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2013/09/23/php-objects-passed-by-reference/
  date: '2013-09-23 03:39:01 -0500'
  date_gmt: '2013-09-23 03:39:01 -0500'
  content: "[&#8230;] a previous post, I mentioned that arrays in PHP are passed by
    [&#8230;]"
---
Apparently arrays in PHP are passed by value, not by reference as you would intuitively think. To illustrate, consider the following snippet of PHP code:

{% highlight php %}
<?php
$a = array(1, 2, 3);
$b = $a;             //This actually creates a copy
$b[1] = 3;           //This does not affect $a
var_dump($a);
var_dump($b);
?>
{% endhighlight %}

When `$b` is assigned `$a`, PHP actually first creates a copy of the array `$a`, then assign the new array to `$b`. Essentially when `$b` is modified, `$a` is unaffected. The output of the code above follows:

{% highlight php %}
array(3) { [0] => int(1) [1] => int(2) [2] => int(3) }
array(3) { [0] => int(1) [1] => int(3) [2] => int(3) }
{% endhighlight %}

I learned this the hard way and spent too much time figuring out what was wrong with my code.

Interesting and confusing enough, class instance objects are passed by reference.

---<br />
<a href="http://stackoverflow.com/questions/2030906/are-arrays-in-php-passed-by-value-or-by-reference" target="_blank">http://stackoverflow.com/questions/2030906/are-arrays-in-php-passed-by-value-or-by-reference</a><br />
<a href="http://stackoverflow.com/questions/2715026/are-php5-objects-passed-by-reference" target="_blank">http://stackoverflow.com/questions/2715026/are-php5-objects-passed-by-reference</a>