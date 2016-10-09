---
layout: post
title: Interleaving String
categories: lintcode
tags:
- Java
- Algorithm
- Longest Common Subsequence
- Dynamic Programming
---

Given three strings: `s1`, `s2`, `s3`, determine whether `s3` is formed by the interleaving of `s1` and `s2`.

Example

```
s1       s2       s3            Return
ab       cd       abcd          true
ab       cd       acdb          true
ab       cd       aabcd         false        
aabcc    dbbca    aadbbcbcac    true
aabcc    dbbca    aadbbbaccc    false
```

{% highlight java %}
public class Solution {
    String a, b, c;
    
    public boolean isInterleave(String s1, String s2, String s3) {
        if (s1.length() + s2.length() != s3.length())
            return false;
            
        a = s1; b = s2; c = s3;
        return dfs(0, 0, 0);
    }
    
    boolean dfs(int i, int j, int k) {
        if (i == a.length() && j == b.length())
            return true;
            
        boolean x = i < a.length() && a.charAt(i) == c.charAt(k) ?
            dfs(i + 1, j, k + 1) : false;
        boolean y = j < b.length() && b.charAt(j) == c.charAt(k) ?
            dfs(i, j + 1, k + 1) : false;
        
        return x || y;
    }
}
{% endhighlight %}
