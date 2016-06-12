---
layout: post
status: publish
published: true
title: Length of Last Word
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1549
wordpress_url: http://codenuggets.com/?p=1549
date: '2016-03-13 03:01:29 -0500'
date_gmt: '2016-03-13 03:01:29 -0500'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- string
comments: []
---
Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

If the last word does not exist, return 0.

A word is defined as a character sequence consists of non-space characters only.

**Example**

Given `s = "Hello World"`, return `5`.

## Solution

This is a simple string processing problem with many ways of solving it. Here we present a simple algorithm.

The idea is to find the start and end index of the last word. Remember the string could have trailing spaces, so the last word doe not necessary ends at the last index of the string.

The Java implementation of the algorithm follows.

{% highlight java %}
public class Solution {
    /**
     * @param s A string
     * @return the length of last word
     */
    public int lengthOfLastWord(String s) {
        if(s == null || s.length() == 0)
            return 0;
        
        int start = -1, end = -1;
        
        //Scan the string from the end to the beginning
        for(int i = s.length() - 1; i >= 0; i--) {
            //If the current character is a space, we have two choices
            //1. If end is -1, the current character is a trailing space, so ignore
            //2. If end is not -1, then we, found the start of last work, end search
            if(s.charAt(i) == ' ') {
                if(end != -1) {
                    start = i;
                    break;
                }
            }
            //If current character is not a space, we have two choices
            //1. If end is -1, we found the end index
            //2. If end is not -1, it's part of last word; so keep going
            else {
                if(end == -1) {
                    end = i;
                }
            }
        }
        
        //If never found the end index, return 0
        if(end == -1)
            return 0;
            
        return end - start;
    }
}
{% endhighlight %}
