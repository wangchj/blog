---
layout: post
title: O(1) Check Power of 2
categories: lintcode
tags:
- Java
- algorithm
- Bit Manipulation
- Kernighan's Algorithm
---

Using O(1) time to check whether an integer n is a power of 2.

```
n = 1 = 001    Yes, power of 2
n = 4 = 100    Yes, power of 2
n = 5 = 101    No, not power of 2
```

{% highlight java %}
class Solution {
    /*
     * @param n: An integer
     * @return: True or false
     */
    public boolean checkPowerOf2(int n) {
        if(n <= 0)
            return false;
        return (n & (n - 1)) == 0;
    }
}
{% endhighlight %}