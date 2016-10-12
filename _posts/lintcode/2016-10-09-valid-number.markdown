---
layout: post
title: Valid Number
categories: lintcode
tags:
- Java
- Algorithm
- String
- Regular Expression
- LinkedIn
---

Given a string, validate that it is a valid number.


A valid number has the follow parts:

1. Sign: `+` or `-`
2. Whole number part
3. Fraction part
4. Exponent part

For example, for the number `-12.34e5`, the following are the parts:

1. Sign: `-`
2. Whole: `12`
3. Fraction: `.34`
4. Exponent: `e5`

We can construct the grammar for a valid number as follows:

```
Number   = (Sign)Whole(Fraction)(Exponent) | (Sign)Fraction(Exponent)
Sign     = + | -
Whole    = Digits
Fraction = .Digits
Exponent = eDigits
```

Example

```
String    Return
0         true
0.1       true
1.        true
.1        true
.1e12     true
abc       false
1 a       false
2e10      true
```

{% highlight java %}
import java.util.regex.Pattern;

public class Solution {
    public boolean isNumber(String s) {
        s = s.trim();
        
        if (s.equals(""))
            return false;
        
        return
            Pattern.matches("^(\\+|-)?\\d+(\\.\\d*)?(e\\d+)?$", s) ||
            Pattern.matches("^(\\+|-)?\\.\\d+(e\\d+)?$", s);
        
    }
}
{% endhighlight %}