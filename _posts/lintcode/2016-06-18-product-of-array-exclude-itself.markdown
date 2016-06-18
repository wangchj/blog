---
layout: post
title: Product of Array Exclude Itself
categories: lintcode
tags:
- Java
- algorithm
- Forward-Backward Traversal
---

Given an integers array `A` of length `n`, calculate array `B` of length `n`, where `B[i]` is the product all elements of array `A` except `A[i]`. In other words, let `p = A[0] × ... × A[n - 1]`, `B[i] = p / A[i]`. Do the computation without using the division operator.

Example 

```
A = [1, 2, 3]
B = [6, 3, 2]
```

{% highlight java %}
public class Solution {
    /**
     * @param A: Given an integers array A
     * @return: A Long array B and B[i]= A[0] * ... * A[i-1] * A[i+1] * ... * A[n-1]
     */
    public ArrayList<Long> productExcludeItself(ArrayList<Integer> A) {
        long[] forward = new long[A.size()];
        long[] backward = new long[A.size()];
        
        //Products forward:
        //forward[0] = A[0]
        //forward[1] = A[0] * A[1]
        //forward[2] = A[0] * A[1] * A[2]
        
        forward[0] = A.get(0);
        for(int i = 1; i < A.size(); i++)
            forward[i] = A.get(i) * forward[i - 1];
            
        //Products backward:
        //backward[len - 1] = A[len - 1]
        //backward[len - 2] = A[len - 1] * A[len - 2]
        //backward[len - 3] = A[len - 1] * A[len - 2] * A[len - 3]
        
        backward[A.size() - 1] = A.get(A.size() - 1);
        for(int i = A.size() - 2; i >= 0; i--) {
            backward[i] = A.get(i) * backward[i + 1];
        }
        
        ArrayList<Long> res = new ArrayList<Long>();
        for(int i = 0; i < A.size(); i++) {
            if(i == 0 && i == forward.length - 1)
                res.add(1L);
            else if(i == 0)
                res.add(backward[1]);
            else if(i == forward.length - 1)
                res.add(forward[forward.length - 2]);
            else
                res.add(forward[i - 1] * backward[i + 1]);
        }
        
        return res;
    }
}
{% endhighlight %}