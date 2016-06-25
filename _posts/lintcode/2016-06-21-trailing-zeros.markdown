---
layout: post
title: Trailing Zeros
categories: lintcode
tags:
- Java
- Algorithm
- Mathematics
---

Write an algorithm which computes the number of trailing zeros in n factorial in O(log n) time.

Example

11! = 39916800, so the algorithm should return 2.

{% highlight java %}
class Solution {
    /*
     * param n: As desciption
     * return: An integer, denote the number of trailing zeros in n!
     */
    public long trailingZeros(long n) {
        long count = 0;
        while(n >= 5) {
            count += n / 5;
            n /= 5;
        }
        return count;
    }
}
{% endhighlight %}