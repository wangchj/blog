---
layout: post
title: Sort Integers
categories: lintcode
tags:
- Java
- Algorithm
- Sort
---

Given an integer array, sort it in ascending order. Use selection sort, bubble sort, insertion sort or any O(n<sup>2</sup>) algorithm.

Example

```
Unsorted        Sorted
[3, 2, 1]       [1, 2, 3]
[1, 3, 2, 1]    [1, 1, 2, 3]
```

The following implements insertion sort.

{% highlight java %}
public class Solution {
    /**
     * @param A an integer array
     * @return void
     */
    public void sortIntegers(int[] A) {
        for (int i = 0; i < A.length; i++) {
            int j = i;
            while (j > 0 && A[j] < A[j - 1]) {
                //Swap A[j] and A[j - 1]
                A[j] ^= A[j - 1];
                A[j - 1] ^= A[j];
                A[j] ^= A[j - 1];
                j--;
            }
        }
    }
}
{% endhighlight %}