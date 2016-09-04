---
layout: post
title: Integer to Roman
categories: lintcode
tags:
- Java
- Algorithm
- Numbers
- String
---

Given an integer, in the range of 1 to 3999, convert it to a Roman numeral.

More information about Roman numerals can be found on [this Wikipedia page](https://en.wikipedia.org/wiki/Roman_numerals).

Example

```
Input    Output
4        "IV"
12       "XII"
21       "XXI"
99       "XCIX"
1000     "M"
```

{% highlight java %}
public class Solution {
    public String intToRoman(int n) {
        int[] val = {
            1000, 900, 500, 400, 100, 90,
            50, 40, 10, 9, 5, 4, 1
        };
        String[] sym = {
            "M", "CM", "D", "CD", "C", "XC", "L",
            "XL", "X", "IX", "V", "IV", "I"
        };
        
        StringBuilder res = new StringBuilder();
        
        for (int i = 0; i < val.length; i++) {
            int count = n / val[i];
            n %= val[i];
            for (int j = 0; j < count; j++)
                res.append(sym[i]);
        }
        
        return res.toString();
    }
}
{% endhighlight %}