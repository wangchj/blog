---
layout: post
title: Reverse Pairs
categories: lintcode
tags:
- Java
- Algorithm
- Array
- Merge Sort
---

For an array `A`, if `i < j`, and `A [i] > A [j]`, then `(A [i], A [j])` is a reversed pair. Find the total number of reversed pairs in `A`.

Example

```
A                  Reversed Pairs
[1, 2, 4, 3]       (4, 3)
[2, 4, 1, 3, 5]    (2, 1), (4, 1), (4, 3)
```

O(n<sup>2</sup>) solution below.

{% highlight java %}
public class Solution {
    /**
     * @param A an array
     * @return total of reverse pairs
     */
    public long reversePairs(int[] A) {
        long res = 0;
        for (int i = 0; i < A.length - 1; i++)
            for (int j = i + 1; j < A.length; j++)
                if (A[i] > A[j])
                    res++;
        return res;
    }
}
{% endhighlight %}