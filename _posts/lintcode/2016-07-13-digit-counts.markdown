---
layout: post
title: Digit Counts
categories: lintcode
tags:
- Java
- Algorithm
- Enumeration
---

Count the number of occurrences of a digit, `k`, in numbers between `0` to `n`, inclusively. The digit `k` can be `0` to `9`.

Example

Let `n = 12`, `k = 1`, then there are 5 digit `1` in the range from `0` to `n`:

```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```

{% highlight java %}
class Solution {
    /*
     * param k : As description.
     * param n : As description.
     * return: An integer denote the count of digit k in 1..n
     */
    public int digitCounts(int k, int n) {
        int res = 0;
        for (int i = 0; i <= n; i++) {
            res += count(k, i);
        }
        return res;
    }
    
    public int count(int k, int num) {
        if (k == 0 && num == 0)
            return 1;
            
        int res = 0;
        while (num > 0) {
            int r = num % 10;
            num /= 10;
            res += r == k ? 1 : 0;
        }
        return res;
    }
}
{% endhighlight %}