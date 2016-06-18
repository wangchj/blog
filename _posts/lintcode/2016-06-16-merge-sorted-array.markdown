---
layout: post
title: Merge Sorted Array
categories: lintcode
tags:
- Java
- algorithm
- Array
- Sorted Array
- Facebook
---

Given two sorted integer arrays `A` and `B`, merge `B` into `A` as one sorted array. Array `A` has `m` number of elements, and array `B` has `n` number of elements. You may assume that `A` has enough space to hold additional elements from `B`; that is, `A` has length of `m` but has capacity of `m + n`.

Example

```
A = [1, 2, 4, empty, empty], m = 3
B = [3, 5], n = 2
Merge A = [1, 2, 3, 4, 5]
```

{% highlight java %}
class Solution {
    /**
     * @param A: sorted integer array A which has m elements, 
     *           but size of A is m+n
     * @param B: sorted integer array B which has n elements
     * @return: void
     */
    public void mergeSortedArray(int[] A, int m, int[] B, int n) {
        /*
        Examples
        a = {1, 4, 6,_,_}
        b = {3, 5}
        
        a = {1, 4, 6,_,_,_}
        b = {3, 5, 5}
        
        a = {1, 4,_, _}
        b = {3, 5}
        */
        
        //A count of number of places to shift
        int shift = 0;
        
        //Count shift
        int i = 0, j = 0;
        while(i < m && j < n) {
            if(B[j] < A[i]) {
                shift++;
                j++;
            }
            else {
                i++;
            }
        }
        
        //Filling in the trailing values from B. These values can be merged
        //into A without any shifting.
        for(i = A.length - 1, j = B.length - 1;
            j > B.length - 1 - (B.length - shift); //Simplify to (shift - 1)
            i--, j--)
        {
            A[i] = B[j];
        }
        
        //Shift and filling at the same time
        i = m - 1;
        while(shift > 0) {
            //Shift
            A[i + shift] = A[i];
            
            //Copy elements of B to A
            int k = i + shift - 1;
            while(j >= 0 && (i == 0 || B[j] > A[i - 1]))
            {
                A[k] = B[j];
                k--;
                j--;
                shift--;
            }
            i--;
        } 
    }
}
{% endhighlight %}