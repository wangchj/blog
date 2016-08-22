---
layout: post
title: Sort Letters by Case
categories: lintcode
tags:
- Java
- Algorithm
- String
- Sort
- Two Pointers
- LintCode Copyright
---

Given a string which contains only letters. Sort it by lower case first and upper case second.

It's NOT necessary to keep the original order of lower-case letters and upper case letters.

Do it in one-pass and in-place.

Example

```
"abAcD"  =>  "acbAD" or "abcDA"
"AaBb"   =>  "abAB"  or "baBA"
```

{% highlight java %}
public class Solution {
    public void sortLetters(char[] chars) {
        int j = 0; // Position of first upper case letter
        
        // Search for first upper case letter
        for (; j < chars.length; j++)
            if (chars[j] >= 'A' && chars[j] <= 'Z')
                break;
        
        // For each lower case letter, swap with chars[j]
        for (int i = j + 1; i < chars.length; i++) {
            if (chars[i] > 'Z') {
                chars[i] ^= chars[j];
                chars[j] ^= chars[i];
                chars[i] ^= chars[j];
                j++;
            }
        }
    }
}
{% endhighlight %}