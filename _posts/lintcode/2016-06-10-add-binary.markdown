---
layout: post
title: Add Binary
categories: lintcode
tags:
- Java
- algorithm
- modulus operator
- modulo operator
- modulo
- LeetCode
- LintCode
- LintCode easy
- integer
comments: []
---

Given two binary strings, return their sum (also a binary string).

Example

```
a = 11
b = 1

a + b:

  011
+ 001
------
  100  
```

We can use a simple approach that adds one bit at a time. The following code use the following variables.

- `ia`: the current bit of `a`
- `ib`: the current bit of `b`
- `carry`: the carry

{% highlight java %}
public class Solution {
    /**
     * @param a a number
     * @param b a number
     * @return the result
     */
    public String addBinary(String a, String b) {
        StringBuilder res = new StringBuilder();
        int carry = 0;
        int maxLen = Math.max(a.length(), b.length());
        for(int i = maxLen - 1; i >= 0; i--) {
            int ia = i - (maxLen - a.length());
            int ib = i - (maxLen - b.length());
            int da = ia < 0 ? 0 : a.charAt(ia) == '0' ? 0 : 1;
            int db = ib < 0 ? 0 : b.charAt(ib) == '0' ? 0 : 1;
            int s = da + db + carry;
            res.append(s % 2);
            carry = s / 2;
        }
            
        if(carry == 1)
            res.append(1);
         
        if(res.length() == 0)
            res.append(0);
            
        return res.reverse().toString();
    }
}
{% endhighlight %}