---
layout: post
title: Longest Common Prefix
categories: lintcode
tags:
- Java
- Algorithm
- String
- Enumeration
- Basic Implementation
- LintCode Copyright
---

Given k strings, find the longest common prefix (LCP).

Example

For strings `"ABCD"`, `"ABEF"` and `"ACEF"`, the LCP is `"A"`

For strings `"ABCDEFG"`, `"ABCEFG"` and `"ABCEFA"`, the LCP is `"ABC"`

{% highlight java %}
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0)
            return "";
            
        int i = 0;
        while (true) {
            for (int j = 0; j < strs.length; j++) {
                if (strs[j].length() == i ||
                    strs[j].charAt(i) != strs[0].charAt(i))
                    return strs[0].substring(0, i);
            }
            i++;
        }
    }
}
{% endhighlight %}