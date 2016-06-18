---
layout: post
title: Search Insert Position in Sorted Array
categories: lintcode
tags:
- Java
- algorithm
- Array
- Sorted Array
- Binary Search
---

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order. Assume that there are NO duplicates in the array. This should be done in O(log n) time.

Example

```
Array       Target      Result
[1,3,5,6]      5          2
[1,3,5,6]      2          1
[1,3,5,6]      7          4
[1,3,5,6]      0          0
```

{% highlight java %}
public class Solution {
    /** 
     * param A : an integer sorted array
     * param target :  an integer to be inserted
     * return : an integer
     */
    public int searchInsert(int[] A, int target) {
        int left = 0;
        int right = A.length - 1;
        while(left <= right) {
            int mid = (right - left) / 2 + left;
            if(A[mid] == target)
                return mid;
            if(A[mid] < target) {
                if(mid == right)
                    return right + 1;
                else
                    left = mid + 1;
            }
            else {
                if(mid == left)
                    return mid;
                else
                    right = mid - 1;
            }
        }
        //This should never be reached
        return 0;
    }
}
{% endhighlight %}