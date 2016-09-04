---
layout: post
title: Sort Colors
categories: lintcode
tags:
- Java
- Algorithm
- Two pointers
- Sort
- Array
- Facebook
---

Given an array with `n` objects colored, `red`, `white` or `blue`, represented by `0`, `1`, and `2` respectively, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

You are not suppose to use the library's sort function for this problem.  You should do it in-place (sort numbers in the original array).

Example

```
Input           Output
[1, 0, 1, 2]    [0, 1, 1, 2]
[2, 2, 0, 2]    [0, 2, 2, 2]
```

The following algorithm uses counting sort.

{% highlight java %}
class Solution {
    
    int[] count = new int[3];
    
    public void sortColors(int[] nums) {
        for (int i : nums)
            count[i]++;
        
        for (int i = 0; i < nums.length; i++) {
            if(i < count[0])
                nums[i] = 0;
            else if(i < count[0] + count[1])
                nums[i] = 1;
            else
                nums[i] = 2;
        }
    }
}
{% endhighlight %}