---
layout: post
title: Find Minimum in Rotated Sorted Array
categories: lintcode
tags:
- Java
- Algorithm
- Heap
---

Suppose a sorted array is rotated at some pivot unknown to you beforehand (i.e., `[0, 1, 2, 4, 5, 6, 7]` becomes `[4, 5, 6, 7, 0, 1, 2]`). Find the minimum element.

Example

```
Input           Return
[1, 2, 3, 4]    1
[2, 3, 0, 1]    0 
```

The following algorithm uses binary search, which has the time complexity of O(log n), where n is the number of elements.

{% highlight java %}
public class Solution {
    public int findMin(int[] nums) {
        int left = 0;
        int right = nums.length - 1;
        
        while (left < right) {
            int mid = (right - left) / 2 + left;
            
            if (mid < right && nums[mid] > nums[mid + 1])
                return nums[mid + 1];
            if (mid > left && nums[mid] < nums[mid - 1])
                return nums[mid];
            
            if (nums[right] <= nums[mid])
                left = mid + 1;
            else
                right = mid - 1;
        }
        
        return nums[left];
    }
}
{% endhighlight %}
