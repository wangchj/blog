---
layout: post
title: Unique Paths In A Grid With Obstacles
categories: lintcode
tags:
- Java
- algorithm
- Dynamic Programming
- Array
---

A robot is located at the top-left corner of a `m x n` grid and trying to reach the bottom-right corner. The grid consists of open spots that are marked with `0`, and obstables that are marked with `1`. The robot can only move through open spots and either down or right at any point in time. How many possible unique paths are there?

Example

```
There is one obstacle in the middle of a 3x3 grid as illustrated below.

[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]

The number of unique paths is 2.
```

{% highlight java %}
public class Solution {
    /**
     * @param obstacleGrid: A list of lists of integers
     * @return: An integer
     */
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int r = obstacleGrid.length, c = obstacleGrid[0].length;
        int[][] s = new int[r][c];
        for(int i = 0; i < r; i++) {
            for(int j = 0; j < c; j++) {
                if(obstacleGrid[i][j] == 1)
                    s[i][j] = 0;
                else {
                    if(i == 0 && j == 0)
                        s[i][j] = 1;
                    else if (i == 0)
                        s[i][j] = s[i][j - 1];
                    else if (j == 0)
                        s[i][j] = s[i - 1][j];
                    else
                        s[i][j] = s[i - 1][j] + s[i][j - 1];
                }
            }
        }
        return s[r - 1][c - 1];
    }
}
{% endhighlight %}