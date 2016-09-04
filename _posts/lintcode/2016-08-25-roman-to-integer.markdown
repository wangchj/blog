---
layout: post
title: Integer to Roman
categories: lintcode
tags:
- Java
- Algorithm
- Numbers
- String
- Uber
---

Given a roman numeral, convert it to an integer.

The answer is guaranteed to be within the range from 1 to 3999.

More information about Roman numerals can be found on [this Wikipedia page](https://en.wikipedia.org/wiki/Roman_numerals).

Example

```
Input    Output
"IV"     4
"XII"    12
"XXI"    21
"XCIX"   99
"M"      1000
```

{% highlight java %}
public class Solution {
    public int romanToInt(String s) {
        int res = 0;
        
        for (int i = 0; i < s.length(); i++) {
            int a = valueOf(s.charAt(i));
            int b = i == s.length() - 1 ? 0 : valueOf(s.charAt(i + 1));
            
            if (a < b) {
                res += b - a;
                i++;
            }
            else {
                res += a;
            }
        }
        
        return res;
    }
    
    int valueOf(char c) {
        if (c == 'M') return 1000;
        if (c == 'D') return 500;
        if (c == 'C') return 100;
        if (c == 'L') return 50;
        if (c == 'X') return 10;
        if (c == 'V') return 5;
        if (c == 'I') return 1;
        return 0;
    }
}
{% endhighlight %}