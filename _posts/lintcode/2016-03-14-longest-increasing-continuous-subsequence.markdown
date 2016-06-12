---
layout: post
status: publish
published: true
title: Longest Increasing Continuous Subsequence
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1556
wordpress_url: http://codenuggets.com/?p=1556
date: '2016-03-14 23:26:50 -0500'
date_gmt: '2016-03-14 23:26:50 -0500'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- array
comments: []
---
Give an integer array，find the longest increasing continuous subsequence in this array.

An increasing continuous subsequence:

Can be from right to left or from left to right.
Indices of the integers in the subsequence should be continuous.

O(n) time and O(1) extra space.

## Solution

We can solve this problem using 2 linear scans. The first goes from the beginning of the array to the end; the other in reverse direction. During the scan, we count the continuous increasing elements, and the longest sequence.

A Java implementation of this algorithm follows.

{% highlight java %}
public class Solution {
    /**
     * @param A an array of Integer
     * @return  an integer
     */
    public int longestIncreasingContinuousSubsequence(int[] A) {
        if(A == null || A.length == 0)
            return 0;
            
        //The max length (scanning forward)
        int a = 1;
        //The current subsequence length
        int count = 1;

        //Scan the array forward
        for(int i = 1; i <; A.length; i++) {
            if(A[i] >= A[i - 1]) {
                count++;
                if(count > a)
                    a = count;
            }
            else {
                count = 1;
            }
        }
        
        //The max length (scanning backwoard)
        int b = 1;
        count = 1;
        
        //Scan the array backward
        for(int i = A.length - 2; i >= 0; i--) {
            if(A[i] >= A[i + 1]) {
                count++;
                if(count > b)
                    b = count;
            }
            else {
                count = 1;
            }
        }
        
        //Return the max of max
        return Math.max(a, b);
    }
}
{% endhighlight %}