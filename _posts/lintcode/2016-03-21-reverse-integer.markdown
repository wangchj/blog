---
layout: post
status: publish
published: true
title: Reverse Integer
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1579
wordpress_url: http://codenuggets.com/?p=1579
date: '2016-03-21 16:23:49 -0500'
date_gmt: '2016-03-21 16:23:49 -0500'
categories: lintcode
tags:
- Java
- algorithm
- modulus operator
- modulo operator
- modulo
- LeetCode
- LintCode
- LintCode easy
- integer
comments: []
---
Reverse digits of an integer. Returns 0 when the reversed integer overflows (signed 32-bit integer).

**Example**

Given x = 123, return 321

Given x = -123, return -321

## Solution

To reverse an integer, we can perform the following steps, assume variable `a` is our result:

1. Get the least digit by performing `r = n % 10`, the remainder operator
2. Add the least digit to our result: `a = a + r`
3. Divide n by 10: `n = n / 10`
4. Multiply a by 10, and repeat for next digit

One gotcha is that the reversed integer could overflow an `int`. There are two ways to solve this:

1. Save the result in a `long` instead of an `int`. At the end of reversal, check to see if the result is greater than `Integer.MAX_VALUE`
2. Check for overflow before multiplication or addition. If overflow will occur, then return error.

In the code below, we choose option 2 of checking overflow.

A Java implementation of this algorithm follows.

{% highlight java %}
public class Solution {
    /**
     * @param n the integer to be reversed
     * @return the reversed integer
     */
    public int reverseInteger(int n) {
        boolean neg = n < 0;
        
        if(neg)
            n = 0 - n; //Absolute value of n
        
        //Accumulator
        int a = 0;
        
        while(n != 0) {
            //Get the least significant digit, r
            int r = n % 10;

            //Discard least significant digit from n
            n /= 10;
            
            //Check for multiplication overflow
            if(a > Integer.MAX_VALUE / 10)
                return 0;
            
            //Shift result by one digit to the left
            a *= 10;
            
            //Check for addition a+=r overflow
            if(r > Integer.MAX_VALUE - a)
                return 0;
            
            //Add the least digit to result
            a += r;
        }
        
        if(neg)
            return -1 * a;
        return a;
    }
}
{% endhighlight %}