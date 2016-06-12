---
layout: post
status: publish
published: true
title: Count 1 in Binary
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1567
wordpress_url: http://codenuggets.com/?p=1567
date: '2016-03-18 18:11:55 -0500'
date_gmt: '2016-03-18 18:11:55 -0500'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- Kernighan
- binary
- bit manipulation
comments: []
---
Count how many 1 in binary representation of a 32-bit integer.

**Example**

Given 32, return 1

Given 5, return 2

Given 1023, return 9

**Challenge**

If the integer is n bits with m 1 bits. Can you do it in O(m) time?

## Solution

We can use Kernighan's bit counting algorithm, which works as follows.

1. The expression `num & (num - 1)` removes a 1 bit from the num
2. Using this fact, we can use the expression in a loop and check for `num == 0`

A Java implementation of the algorithm is below.

{% highlight java %}
public class Solution {
    /**
     * @param num: an integer
     * @return: an integer, the number of ones in num
     */
    public int countOnes(int num) {
        int res = 0;
        while(num != 0) {
            res++;
            num &= num - 1;
        }
        return res;
    }
}
{% endhighlight %}
