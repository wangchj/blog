---
layout: post
status: publish
published: true
title: Partition Array by Odd and Even
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1558
wordpress_url: http://codenuggets.com/?p=1558
date: '2016-03-18 03:30:28 -0500'
date_gmt: '2016-03-18 03:30:28 -0500'
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
Partition an integers array into odd number first and even number second.

Example:

Given `[1, 2, 3, 4]`, return `[1, 3, 2, 4]`

## Solution

One simple solution is the swap method. We first find the position of the first even number in the array. Then for every odd number that follows, we swap the odd number with the position of the even number. This time complexity of this algorithm is O(n). 

A Java implementation follows.

{% highlight java %}
public class Solution {
    /**
     * @param nums: an array of integers
     * @return: nothing
     */
    public void partitionArray(int[] nums) {
        /*Examples
        3 2 5 4
        */
        
        //The position of the first even
        int even = 0;
        
        //Look for the first even
        for(even = 0; even < nums.length; even++) {
            if(nums[even] % 2 == 0)
                break;
        }
        
        //For every odd, swap place with nums[even]
        for(int i = even + 1; i < nums.length; i++) {
            if(nums[i] % 2 != 0) {
                //Swap without temporary variable
                nums[even] ^= nums[i];
                nums[i] ^= nums[even];
                nums[even] ^= nums[i];
                even++;
            }
        }
    }
}
{% endhighlight %}