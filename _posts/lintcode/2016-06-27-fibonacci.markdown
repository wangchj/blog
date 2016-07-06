---
layout: post
title: Fibonacci
categories: lintcode
tags:
- Java
- Algorithm
- Mathematics
- Enumeration
- Non-recursion
---

Give an integer `n`, write a function `fibonacci(n)` that finds the n-th Fibonacci's number.

The `fibonacci(n)` function is defined as follows:

- `fibonacci(1) = 0` and `fibonacci(2) = 1` 
- `fibonacci(i) = fibonacci(i - 1) + fibonacci(i - 2)`

The first ten numbers in Fibonacci sequence is:

`0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...`

Example

```
N     Result
1     0
2     1
3     1
4     2
10    34
```

{% highlight java %}
class Solution {
    /**
     * @param n: an integer
     * @return an integer f(n)
     */
    public int fibonacci(int n) {
        if(n == 1)
            return 0;
        if(n == 2)
            return 1;
            
        int a = 0;
        int b = 1;
        
        int res = 0;
        
        for(int i = 3; i <= n; i++) {
            res = a + b;
            a = b;
            b = res;
        }
        
        return res;
    }
}
{% endhighlight %}