---
layout: post
title: Ugly Number
categories: lintcode
tags:
- Java
- Algorithm
- Mathematics
---

Write a program to check whether a given number is an ugly number. Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7. One is also considered an ugly number.

Example

```
num    factors    result
1      1          true
8      2*2*2      true
14     2*7        false
```

{% highlight java %}
public class Solution {
    /**
     * @param num an integer
     * @return true if num is an ugly number or false
     */
    public boolean isUgly(int num) {
        if (num == 0)
            return false;
            
        while (num % 2 == 0)
            num /= 2;
        while (num % 3 == 0)
            num /= 3;
        while (num % 5 == 0)
            num /= 5;
        return num == 1;
    }
}
{% endhighlight %}