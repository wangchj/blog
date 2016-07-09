---
layout: post
title: Find the Missing Number
categories: lintcode
tags:
- Java
- Algorithm
- Mathematics
---

Given an array contains N numbers of `0 .. N`, find which number doesn't exist in the array.

Example

```
Array                 Missing
[1, 3]                2
[1, 2, 4]             3
[1, 2, 3, 5, 6, 7]    4
```

{% highlight java %}
public class Solution {
    /**    
     * @param nums: an array of integers
     * @return: an integer
     */
    public int findMissing(int[] nums) {
        int res = 0;
        for(int i = 1; i <= nums.length; i++)
            res ^= i;
        for(int i = 0; i < nums.length; i++)
            res ^= nums[i];
        return res;
    }
}
{% endhighlight %}