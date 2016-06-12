---
layout: post
status: publish
published: true
title: Subarray Sum to Zero
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1514
wordpress_url: http://codenuggets.com/?p=1514
date: '2016-03-06 08:05:42 -0600'
date_gmt: '2016-03-06 08:05:42 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- HashMap
- array
- subarray
- hash table
comments: []
---
Given an integer array, find a subarray where the sum of numbers is zero. Your code should return the index of the first number and the index of the last number.

The subarray should contain at least one integer.

**Example**

Given `[-3, 1, 2, -3, 4]`, return `[0, 2]` or `[1, 3]`.

## Solution

A simple solution is to have two array index pointers and check every possible subarray. When a subarray sums to 0, we return the two index pointers as the result. This algorithm has O(n<sup>2</sup>) time complexity and we can do better.

A more efficient algorithm is to keep a running sum from the beginning of the array and use an HashMap to track the running sum for each index of the array, as shown in the figure below.

```
nums: -3  1  2 -3  4
sum : -3 -2  0 -3  1

nums:  3  2 -1 -1  1
sum :  3  5  4  3  4
```

There are two scenario where we found the zero-sum subarray:

1. When the running sum is 0. In this case, we know the zero-sum subarray is from index 0 to the current index.
2. When a sum is already in the HashMap. In this case, the subarray between the index where we last found the sum to the current index, is a zero-sum subarray, because this subarray essentially contributed nothing to the running sum.

This algorithm has time complexity of O(n) and the implementation is listed below.

{% highlight java %}
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A list of integers includes the index of the first number 
     *          and the index of the last number
     */
    public ArrayList<Integer> subarraySum(int[] nums) {
        //A map that maps sum -> index
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        //The list to be returned
        ArrayList<Integer> res = new ArrayList<Integer>();
        //Running sum
        int sum = 0;
        
        for(int i = 0; i < nums.length; i++) {
            sum += nums[i];
            
            //If the sum is 0, we found the zero-sum subarray.
            if(sum == 0) {
                res.add(0);
                res.add(i);
                return res;
            }
            
            //If the current sum is already in the HashMap, that means the
            //subarray between the index we last encountered this sum and
            //i is a zero-sum subarray. Because the sum of this subarray
            //has no effect (0), so we get the same sum.
            if(map.containsKey(sum)) {
                res.add(map.get(sum) + 1);
                res.add(i);
                return res;
            }
            
            //The map does not contain the sum. Add the current sum to the
            //map.
            map.put(sum, i);
        }
        
        return res;
    }
}
{% endhighlight %}