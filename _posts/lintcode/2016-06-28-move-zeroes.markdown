---
layout: post
title: Move Zeroes
categories: lintcode
tags:
- Java
- Algorithm
- Array
---

Given an array `nums`, write a function to move all 0's to the end of the array. The operation should be done in-place without making a copy of the array and the non-zero elements should stay in  the original relative order.

Example

```
[0, 1, 0, 3, 12] => [1, 3, 12, 0, 0]
```

{% highlight java %}
public class Solution {
    /**
     * @param nums an integer array
     * @return nothing, do this in-place
     */
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length == 0)
            return;
        for (int i = nums.length - 1; i >= 0; i--) {
            if (nums[i] == 0) {
                int j = i;
                while (j < nums.length - 1 && nums[j + 1] != 0) {
                    nums[j] ^= nums[j + 1];
                    nums[j + 1] ^= nums[j];
                    nums[j] ^= nums[j + 1];
                    j++;
                }
            }
        }
    }
}
{% endhighlight %}