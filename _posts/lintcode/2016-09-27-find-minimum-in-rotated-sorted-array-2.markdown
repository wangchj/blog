---
layout: post
title: Find Minimum in Rotated Sorted Array II
categories: lintcode
tags:
- Java
- Algorithm
- Binary Search
---

This is follow up to [Find Minimum in Rotated Sorted Array](/lintcode/find-minimum-in-rotated-sorted-array). Suppose a sorted array is rotated at some pivot unknown to you beforehand, and duplicates are allowed. Find the minimum element.

Example

```
Input           Return
[1, 1, 3, 4]    1
[2, 3, 0, 2]    0
```

The following uses the same approach as the previous problem. The only difference is that, when `num[left]` equals `num[right]`, we can drop one of them. The worse case time complexity is O(n).

{% highlight java %}
public class Solution {
    public int findMin(int[] num) {
        int left = 0;
        int right = num.length - 1;
        
        while (left < right) {
            int mid = (right - left) / 2 + left;
            
            if (mid < right && num[mid] > num[mid + 1])
                return num[mid + 1];
            if (mid > left && num[mid] < num[mid - 1])
                return num[mid];

            if (num[right] < num[mid])
                left = mid + 1;
            else if (num[right] == num[left]) // Drop left
                left++;
            else
                right = mid - 1;
        }
        
        return num[left];
    }
}
{% endhighlight %}
