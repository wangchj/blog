---
layout: post
status: publish
published: true
title: Space Replacement
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1541
wordpress_url: http://codenuggets.com/?p=1541
date: '2016-03-11 02:24:39 -0600'
date_gmt: '2016-03-11 02:24:39 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- string
- Cracking the Coding Interview
comments: []
---
Write a method to replace all spaces in a string with %20. The string is given in a characters array, you can assume it has enough space for replacement and you are given the true length of the string.

You code should also return the new length of the string after replacement.

Given "Mr John Smith", length = 13.

The string after replacement should be "Mr%20John%20Smith" and return 17.

## Discussion

An easy solution to this problem is to scan the string. Whenever we encounter a space, we shift the characters after the space 2 places and fill in "%20". This algorithm works; however, there is a lot of repeated shifting of the same characters. The time complexity of this algorithm is O(n<sup>2</sup>).

A better algorithm is that we do all the shifting once; so we don't have to shift the same characters multiple times. To do so, we need to know the number of spaces in the string; so we know how many spaces to shift. For example, if the string only has 1 space, then we know that we only need to shift 2 positions. If the string has 2 spaces, then we need to shift 4 positions.

With this idea in mind, we have the algorithm:

1. Count the number of spaces in the string
2. Scan the string backward.
    1. For every non-space, shift that character `count * 2` positions
    2. For a space, fill in "%20", and decrement count by 1
3. At the end, return the new length which is `length + 2 * space_count`

The time complexity of this algorithm is O(n).

A Java implementation of this algorithm follows.

{% highlight java %}
public class Solution {
    /**
     * @param string: An array of Char
     * @param length: The true length of the string
     * @return: The true length of new string
     */
    public int replaceBlank(char[] string, int length) {
        int spaces = countSpace(string, length);
        int res = length + 2 * spaces;
        for(int i = length - 1; i >= 0; i--) {
            if(string[i] == ' ') {
                string[spaces * 2 + i] = '0';
                string[spaces * 2 + i - 1] = '2';
                string[spaces * 2 + i - 2] = '%';
                spaces--;
            }
            else {
                string[spaces * 2 + i] = string[i];
            }
        }
        return res;
    }
    
    private int countSpace(char[] string, int length) {
        int res = 0;
        for(int i = 0; i < length; i++)
            if(string[i] == ' ')
                res++;
        return res;
    }
}
{% endhighlight %}
