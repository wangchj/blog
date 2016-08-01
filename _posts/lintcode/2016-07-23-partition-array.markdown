---
layout: post
title: Partition Array
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sort
- Two Pointers
---

Given an array `nums` of integers and an integer `k`, partition the array (i.e move the elements in "nums") such that:

- All elements < k are moved to the left
- All elements >= k are moved to the right
- Each partition does not have to be in specific order

Return the partitioning index, i.e the first index `i` where `nums[i] >= k`.

Example

```
Array           k    Result          Return
[4, 3, 2, 1]    2    [1, 2, 4, 3]    1
[4, 3, 2, 1]    1    [1, 2, 4, 3]    0
[4, 3, 2, 1]    3    [1, 2, 3, 4]    2
```

{% highlight java %}
public class Solution {
    /** 
     *@param nums: The integer array you should partition
     *@param k: As description
     *return: The index after partition
     */
    public int partitionArray(int[] nums, int k) {
        int res = 0;
        
        //Find the first num >= k
        while (res < nums.length && nums[res] < k)
            res++;
        
        for (int i = res + 1; i < nums.length; i++) {
            if (nums[i] < k) {
                //Swap
                nums[res] ^= nums[i];
                nums[i] ^= nums[res];
                nums[res] ^= nums[i];
                //Increment res
                res++;
            }
        }
        
        return res;
    }
}
{% endhighlight %}