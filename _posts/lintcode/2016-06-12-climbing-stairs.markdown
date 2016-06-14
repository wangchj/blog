---
layout: post
title: Climbing Stairs
categories: lintcode
tags:
- Java
- algorithm
- Dynamic Programming
---

You are climbing a stair case. It takes `n` steps to reach to the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Example

```
                                                ┌───
                                                │
                            ┌───            ┌───┘
                            │               │
            ┌───        ┌───┘           ┌───┘
            │           │               │
┌───    ┌───┘       ┌───┘           ┌───┘
│       │           │               │

n = 1    n = 2          n = 3             n = 4
r = 1    r = 2          r = 3             r = 5
```

The solution is nothing but computing Fibonacii's Number of `n`.

{% highlight java %}
public class Solution {
    /**
     * @param n: An integer
     * @return: An integer
     */
    public int climbStairs(int n) {
        //Calcuate fibonacii's number using O(n) approach
        int a = 1, b = 1, s = 1;
        for(int i = 1; i < n; i++) {
            s = a + b;
            a = b;
            b = s;
        }
        return s;
    }
}
{% endhighlight %}