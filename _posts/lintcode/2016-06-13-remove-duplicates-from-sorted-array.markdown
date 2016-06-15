---
layout: post
title: Remove Duplicates from Sorted Array
categories: lintcode
tags:
- Java
- algorithm
- Two Pointers
- Array
- Facebook
---

Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length. Do not allocate extra space for another array, you must do this in place with constant memory.

Example

```
A = [1, 1, 2, 3, 3, 4], length = 6

    Becomes 

A = [1, 2, 3, 4, x, x], length = 4
```

{% highlight java %}
public class Solution {
    /**
     * @param A: a array of integers
     * @return : return an integer
     */
    public int removeDuplicates(int[] nums) {
        int dup = 0;
        int len = nums.length;
        for(int i = 1; i < nums.length; i++) {
            if(nums[i] == nums[i - 1]) {
                dup++;
                len--;
            }
            else {
                if(dup == 0)
                    continue;
                nums[i - dup] = nums[i];
            }
        }
        return len;
    }
}
{% endhighlight %}