---
layout: post
title: Maximum Subarray
categories: lintcode
tags:
- Java
- Algorithm
- Greedy
- Array
- Subarray
- Enumeration
- LinkedIn
---

Given an array of integers, find the contiguous subarray with the largest sum and return the sum. The subarray should contain at least one element from the array.

Example

```
A = [-2, 2, -3, 4, -1, 2, 1, -5, 3]  =>  Max sum = 6
```

Can you do it in O(n) time?

{% highlight java %}
public class Solution {
    /**
     * @param nums: A list of integers
     * @return: A integer indicate the sum of max subarray
     */
    public int maxSubArray(int[] nums) {
        if(nums.length == 0)
            return 0;
        int max = nums[0];
        int sum = nums[0];
        for(int i = 1; i < nums.length; i++) {
            if(nums[i] + sum < nums[i])
                sum = nums[i];
            else
                sum += nums[i];
            if(sum > max)
                max = sum;
        }
        return max;
    }
}
{% endhighlight %}