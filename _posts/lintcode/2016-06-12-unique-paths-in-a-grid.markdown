---
layout: post
title: Unique Paths In A Grid
categories: lintcode
tags:
- Java
- algorithm
- Dynamic Programming
- Array
---

A robot is located at the top-left corner of a `m x n` grid. The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid. How many possible unique paths are there?

Example

```
m = 2, n = 2

+---+---+
|   |   |
+---+---+    There are 2 unique paths
|   |   |
+---+---+
```

{% highlight java %}
public class Solution {
    /**
     * @param n, m: positive integer (1 <= n ,m <= 100)
     * @return an integer
     */
    public int uniquePaths(int m, int n) {
        int[][] s = new int[m][n];
        for(int i = 0; i < m; i++) {
            for(int j = 0; j < n; j++) {
                if(i == 0 || j == 0)
                    s[i][j] = 1;
                else
                    s[i][j] = s[i - 1][j] + s[i][j - 1];
            }
        }
        return s[m - 1][n - 1];
    }
}
{% endhighlight %}