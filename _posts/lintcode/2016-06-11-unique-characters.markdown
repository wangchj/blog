---
layout: post
title: Unique Characters
categories: lintcode
tags:
- Java
- algorithm
- Kernighma's Algrithm
- String
- Array
- Cracking The Coding Interview
comments: []
---

Implement an algorithm to determine if a string has all unique characters.

Example

```
"abc" -> unique characters
"aab" -> not unique characters
```

The following does not use additional data structure. However, the running time is O(n<sup>2</sup>).

{% highlight java %}
public class Solution {
    /**
     * @param str: a string
     * @return: a boolean
     */
    public boolean isUnique(String str) {
        //if(str.length() > 26)
        //    return false;
        for(int i = 0; i < str.length(); i++) {
            for(int j = i + 1; j < str.length(); j++) {
                if(str.charAt(i) == str.charAt(j))
                    return false;
            }
        }
        return true;
    }
}
{% endhighlight %}