---
layout: post
status: publish
published: true
title: Count and Say
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1552
wordpress_url: http://codenuggets.com/?p=1552
date: '2016-03-13 03:36:55 -0500'
date_gmt: '2016-03-13 03:36:55 -0500'
categories: lintcode
tags:
- Java
- interview
- algorithm
- LeetCode
- LintCode
- Facebook
- LintCode easy
- string
- practice
comments: []
---
The count-and-say sequence is the sequence of integers beginning as follows:

`1, 11, 21, 1211, 111221, ...`

1 is read off as "one 1" or 11.

11 is read off as "two 1s" or 21.

21 is read off as "one 2, then one 1" or 1211.

Given an integer n, generate the nth sequence.

Example:

Given n = 5, return `"111221"`.

## Solution

For this problem, we can define a mutate() method that does the transformation. For n = 1, we can just return the string `"1"`. For n larger than 1, we just call mutate() n - 1 times.

The mutate() method simply counts the numbers in each cluster and outputs a string.

The Java implementation follows.

{% highlight java %}
public class Solution {
    /**
     * @param n the nth
     * @return the nth sequence
     */
    public String countAndSay(int n) {
        String res = "1";
        if(n == 1)
            return res;
        for(int i = 1; i < n; i++) {
            res = mutate(res);
        }
        return res;
    }
    
    private String mutate(String s) {
        StringBuilder res = new StringBuilder();
        char c = s.charAt(0);
        int count = 1;
        for(int i = 1; i < s.length(); i++) {
            if(s.charAt(i) == s.charAt(i - 1)) {
                count++;
            }
            else {
                res.append(count);
                res.append(c);
                
                c = s.charAt(i);
                count = 1;
            }
        }
        res.append(count);
        res.append(c);
        return res.toString();
    }
}
{% endhighlight %}
