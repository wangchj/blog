---
layout: post
title: Longest Common Subsequence
categories: lintcode
tags:
- Java
- Algorithm
- Longest Common Subsequence
- Recursion
- Dynamic Programming
---

Given two strings, find the length of the longest common subsequence (LCS).

Example

```
A         B         LCS     Length
"ABCD"    "EDCA"    "A"     1
"ABCD"    "EACB"    "AC"    2
```

I got Time Limit Exceeded for the following simple recursive solution.

{% highlight java %}
public class Solution {
    public int longestCommonSubsequence(String a, String b) {
        if (a == null || b == null)
            return 0;
        return lcs(a, b, 0, 0);
    }
    
    int lcs(String a, String b, int i, int j) {
        if (i == a.length() || j == b.length())
            return 0;
        if (a.charAt(i) == b.charAt(j)) {
            return 1 + lcs(a, b, i + 1, j + 1);
        }
        else {
            return Math.max(lcs(a, b, i + 1, j), lcs(a, b, i, j + 1));
        }
    }
}
{% endhighlight %}

The following uses dynamic programming and follows the algorithm described in [this article](https://en.wikipedia.org/wiki/Longest_common_subsequence_problem). This solution is accepted.

{% highlight java %}
public class Solution {
    public int longestCommonSubsequence(String a, String b) {
        if (a == null || b == null || a.length() == 0 || b.length() == 0)
            return 0;

        int[][] table = new int[a.length()][b.length()];
        
        for (int i = 0; i < a.length(); i++) {
            for (int j = 0; j < b.length(); j++) {
                if (a.charAt(i) == b.charAt(j)) {
                    if (i == 0 || j == 0)
                        table[i][j] = 1;
                    else
                        table[i][j] = 1 + table[i - 1][j - 1];
                }
                else {
                    int x = i == 0 ? 0 : table[i - 1][j];
                    int y = j == 0 ? 0 : table[i][j - 1];
                    table[i][j] = Math.max(x, y);
                }
            }
        }
        
        return table[a.length() - 1][b.length() - 1];
    }
}
{% endhighlight %}
