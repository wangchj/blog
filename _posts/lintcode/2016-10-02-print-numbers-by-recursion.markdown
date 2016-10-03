---
layout: post
title: Print Numbers by Recursion
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
---

Print numbers from 1 to the largest number with `n` digits by recursion.

It's pretty easy to do recursion like:

```
recursion(i) {
    if i > largest number:
        return
    results.add(i)
    recursion(i + 1)
}
```

However this cost a lot of recursion memory as the recursion depth maybe very large. Can you do it in another way to recursive with at most `n` depth?

Example

Given `n = 1`, return `[1, 2, 3, 4, 5, 6, 7, 8, 9]`.

Given `n = 2`, return `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, ..., 99]`.


{% highlight java %}
public class Solution {
    List<Integer> res = new ArrayList<>();
    
    public List<Integer> numbersByRecursion(int n) {
        rec(n, 1);
        return res;
    }
    
    void rec(int n, int count) {
        if (count > n)
            return;
        
        int lo = (int)Math.pow(10, count - 1);
        int hi = (int)Math.pow(10, count);
        
        for (int i = lo; i < hi; i++)
            res.add(i);
            
        rec(n, count + 1);
    }
}
{% endhighlight %}
