---
layout: post
title: Minimum Path Sum in a Grid
categories: lintcode
tags:
- Java
- algorithm
- Dynamic Programming
---

Given a `m x n` grid filled with non-negative numbers, and only allowing to move either down or right, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Example

```
┌───┬───┬───┐
│ 1 │ 1 │ 3 │
├───┼───┼───┤   Min Path Sum = 1 + 1 + 1 + 1 = 4
│ 2 │ 1 │ 1 │
└───┴───┴───┘
```

{% highlight java %}
public class Solution {
    /**
     * @param grid: a list of lists of integers.
     * @return: An integer, minimizes the sum of all numbers along its path
     */
    public int minPathSum(int[][] grid) {
        if(grid == null || grid.length == 0)
            return 0;
        
        int m = grid.length, n = grid[0].length;
        
        for(int i = 0; i < m; i++) {
            for(int j = 0; j < n; j++) {
                if(i == 0 && j == 0)
                    continue;
                if(i == 0)
                    grid[i][j] += grid[i][j - 1];
                else if(j == 0)
                    grid[i][j] += grid[i - 1][j];
                else
                    grid[i][j] += Math.min(grid[i][j - 1], grid[i - 1][j]);
            }
        }
        return grid[m - 1][n - 1];
    }
}
{% endhighlight %}