---
layout: post
title: Minimum Path Sum in a Triangle
categories: lintcode
tags:
- Java
- algorithm
- Dynamic Programming
---

Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle.

Example

```
[
     [2],
    [3,4],
   [6,5,7],   Min path sum = 2 + 3 + 5 + 1 = 11
  [4,1,8,3]
]
```

Use binary search to find the result.

{% highlight java %}
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    public int minimumTotal(int[][] triangle) {
        if(triangle == null || triangle.length == 0)
            return 0;
            
        for(int i = triangle.length - 2; i >= 0; i--) {
            for(int j = 0; j < triangle[i].length; j++) {
                triangle[i][j] += Math.min(triangle[i + 1][j], triangle[i + 1][j + 1]);
            }
        }
        return triangle[0][0];
    }
}
{% endhighlight %}