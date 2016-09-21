---
layout: post
title: Longest Common Substring
categories: lintcode
tags:
- Java
- Algorithm
- String
- Hash Table
---

Given two strings, return the length of the longest common substring.

The characters in substring should occur continuously in original string. This is different with subsequence.

Example

```
String A    String B    Return
"ABCD"      "DEFG"      1
"ABCD"      "CBCE"      2
```

{% highlight java %}
public class Solution {
    public int longestCommonSubstring(String A, String B) {
        int max = 0;
        Set<String> set = new HashSet<>();
        
        for (int i = 0; i < A.length(); i++)
            for (int j = i + 1; j <= A.length(); j++)
                set.add(A.substring(i, j));
        
        for (int i = 0; i < B.length(); i++) {
            for (int j = i + 1; j <= B.length(); j++) {
                String s = B.substring(i, j);
                if (set.contains(s) && s.length() > max)
                    max = s.length();
            }
        }
        
        return max;
    }
}
{% endhighlight %}