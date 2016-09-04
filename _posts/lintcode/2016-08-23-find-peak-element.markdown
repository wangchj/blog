---
layout: post
title: Find Peak Element
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Binary Search
- Google
---

Given an integer array `A`, a peak element with index `p` is defined as `A[p] > A[p - 1] && A[p] > A[p + 1]`. Find a peak element in this array and return its index. The array may contains multiple peeks; return any of them.

Note, the array has the following properties:

- The numbers in adjacent positions are different.
- A[0] < A[1] && A[A.length - 2] > A[A.length - 1].

Example

Given `[1, 2, 1, 3, 4, 5, 7, 6]`

Return index `1` (which is number 2) or `6` (which is number 7)

The following solution has O(n) time-complexity.

{% highlight java %}
class Solution {
    public int findPeak(int[] A) {
        if (A.length == 1)
            return A[0];
            
        for (int i = 0; i < A.length; i++) {
            if (i == 0) {
                if (A[i + 1] < A[i])
                    return i;
            }
            else if (i == A.length - 1) {
                if (A[i - 1] < A[i])
                    return i;
            }
            else {
                if (A[i - i] < A[i] && A[i + 1] < A[i])
                    return i;
            }
        }
        
        return 0;
    }
}
{% endhighlight %}