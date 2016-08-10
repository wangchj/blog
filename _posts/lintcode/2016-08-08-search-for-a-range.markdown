---
layout: post
title: Search for a Range
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sorted Array
- Binary Search
---

Given a sorted array of n integers, find the starting and ending position of a given target value.

If the target is not found in the array, return `[-1, -1]`.

Example

```
Array           Target    Return
[5, 7, 7, 8]    7         [1, 2]
[5, 7, 7, 8]    9         [-1, -1]
```

{% highlight java %}
public class Solution {
    /** 
     *@param a : an integer sorted array
     *@param target :  an integer to be inserted
     *return : a list of length 2, [index1, index2]
     */
    public int[] searchRange(int[] a, int target) {
        return new int[] {
            searchStart(a, target),
            searchEnd(a, target)  
        };
    }
    
    /**
     * Search start index using binary search.
     * 
     * a[mid] is < target: left = mid + 1;
     * a[mid] is > target: right = mid - 1;
     * a[mid] is = target:
     *   a[mid - 1] != target || mid = 0: found!
     *   a[mid - 1] == target: right = mid - 1
     */
    int searchStart(int[] a, int target) {
        if (a == null || a.length == 0)
            return -1;
            
        int left = 0;
        int right = a.length - 1;
        
        while (left <= right) {
            int mid = (right - left) / 2 + left;
            if (a[mid] < target)
                left = mid + 1;
            else if (a[mid] > target)
                right = mid - 1;
            else {
                if (mid == 0 || a[mid - 1] != target)
                    return mid;
                else
                    right = mid - 1;
            }
        }
        
        return -1;
    }
    
    int searchEnd(int[] a, int target) {
        if (a == null || a.length == 0)
            return -1;
            
        int left = 0;
        int right = a.length - 1;
        
        while (left <= right) {
            int mid = (right - left) / 2 + left;
            if (a[mid] < target)
                left = mid + 1;
            else if (a[mid] > target)
                right = mid - 1;
            else {
                if (mid == a.length - 1 || a[mid + 1] != target)
                    return mid;
                else
                    left = mid + 1;
            }
        }
        
        return -1;
    }
}
{% endhighlight %}