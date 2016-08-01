---
layout: post
title: Rotate String
categories: lintcode
tags:
- Java
- Algorithm
- String
---

Given a string and an offset, rotate string by offset from left to right.

Example

```
String       Offset    Result
[a, b, c]    0         [a, b, c]
[a, b, c]    1         [c, a, b]
[a, b, c]    2         [b, c, a]
[a, b, c]    3         [a, b, c]
```

{% highlight java %}
public class Solution {
    /**
     * @param str: an array of char
     * @param offset: an integer
     * @return: nothing
     */
    public void rotateString(char[] str, int offset) {
        if (str == null || str.length == 0 || offset == 0)
            return;
        offset = offset % str.length;
        for (int i = 0; i < offset; i++)
            rotate(str);
    }
    
    /**
     * Rotate one position to the right.
     */
    private void rotate(char[] str) {
        char temp = str[str.length - 1];
        for (int i = str.length - 2; i >=0; i--)
            str[i + 1] = str[i];
        str[0] = temp;
    }
}
{% endhighlight %}