---
layout: post
title: Merge Two Sorted Arrays
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Sorted Array
---

Merge two given sorted integer array A and B into a new sorted integer array.

Example

```
A = [1, 2, 3, 4] \
                   => [1, 2, 2, 3, 3, 4, 5, 6]
B = [2, 3, 5, 6] /
```

{% highlight java %}
class Solution {
    /**
     * @param A and B: sorted integer array A and B.
     * @return: A new sorted integer array
     */
    public int[] mergeSortedArray(int[] A, int[] B) {
        if (A == null || A.length == 0)
            return B;
        if (B == null || B.length == 0)
            return A;
            
        int[] res = new int[A.length + B.length];
        int i = 0, j = 0, k = 0;
        
        while (i < A.length || j < B.length) {
            if (i == A.length) {
                res[k] = B[j];
                j++;
            }
            else if (j == B.length) {
                res[k] = A[i];
                i++;
            }
            else if (A[i] <= B[j]) {
                res[k] = A[i];
                i++;
            }
            else {
                res[k] = B[j];
                j++;
            }
            k++;
        }
        
        return res;
    }
}
{% endhighlight %}