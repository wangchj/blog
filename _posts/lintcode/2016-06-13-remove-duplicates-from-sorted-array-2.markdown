---
layout: post
title: Remove Duplicates from Sorted Array II
categories: lintcode
tags:
- Java
- algorithm
- Two Pointers
- Array
- Facebook
---

Given a sorted array, remove the duplicates in place such that each element appear only at most twice and return the new length. Do not allocate extra space for another array, you must do this in place with constant memory.

Example

```
A = [1, 1, 1, 2, 3, 3, 4], length = 7

    Becomes 

A = [1, 1, 2, 3, 3, 4, x], length = 6
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
        int i = 0, j = 1;
        
        while(j < nums.length) {
            if(nums[i] == nums[j]) {
                //Checks for the second duplicate
                if(j - i == 1)
                    nums[j - dup] = nums[j];
                        
                //This if statement checks if there are already 3 duplicates
                //because if there are only 2 duplicates, then j - i = 1.
                if(j - i > 1) {
                    dup++;
                    len--;
                }
                j++;
            }
            else {
                //Copy the current value pointed by j to its proper place
                nums[j - dup] = nums[j];
                i = j;
                j++;
            }
        }
        
        return len;
    }
}
{% endhighlight %}