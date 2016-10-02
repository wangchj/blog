---
layout: post
title: Search in Rotated Sorted Array II
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sorted Array
- Binary Search
---

This is a follow up for [Search in Rotated Sorted Array](/lintcode/search-in-rotated-sorted-array). Suppose a sorted array is rotated at some pivot unknown to you beforehand. You are given a target value to search. If found in the array return its index, otherwise return `-1`. Duplicates are allowed in the array.

Would this affect the run-time complexity? How and why?

Write a function to determine if a given target is in the array.

Example

```
Array                 Target    Return
[1, 1, 0, 1, 1, 1]    0         true
[1, 1, 1, 1, 1, 1]    0         false
```

The following algorithm uses binary search. The trick is that when `a[left]` is equal to `a[right]`, we can discard one. In the following code, we discard `a[left]`. The average time complexity is O(log n), but the worse case time complexity is O(n).

{% highlight java %}
public class Solution {
    public boolean search(int[] a, int target) {
        if (a == null || a.length == 0)
            return false;
            
        int left = 0, right = a.length - 1;
        
        while (left <= right) {
            int mid = (right - left) / 2 + left;
            
            if (a[left] == target || a[right] == target ||
                a[mid] == target)
                return true;
            
            if (a[mid] < target) { // Need to go higher
                if (a[right] > a[mid])
                    left = mid + 1;
                else if (a[left] == a[right])
                    left++;
                else
                    right = mid - 1;
            }
            else { // a[mid] > target, need to go lower
                if (a[right] < a[mid])
                    left = mid + 1;
                else if (a[left] == a[right])
                    left++;
                else
                    right = mid - 1;
            }
        }
        return false;
    }
}
{% endhighlight %}
