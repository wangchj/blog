---
layout: post
title: Set Matrix Zeroes
categories: lintcode
tags:
- Java
- Algorithm
- Matrix
- Cracking The Coding Interview
---

Given a `m x n` matrix, if an element is 0, set its entire row and column to 0. Do it in place.

Example

```
Given a matrix 

[1, 2]
[0, 3]

Return 

[0, 2]
[0, 0]
```

{% highlight java %}
public class Solution {
    public void setZeroes(int[][] matrix) {
        if (matrix == null || matrix.length == 0)
            return;
            
        boolean[] row = new boolean[matrix.length];
        boolean[] col = new boolean[matrix[0].length];
        for(int r = 0; r < matrix.length; r++) {
            for(int c = 0; c < matrix[0].length; c++) {
                if(matrix[r][c] == 0) {
                    row[r] = true;
                    col[c] = true;
                }
            }
        }
        
        for(int r = 0; r < matrix.length; r++) {
            for(int c = 0; c < matrix[0].length; c++) {
                if(row[r] || col[c])
                    matrix[r][c] = 0;
            }
        }
    }
}
{% endhighlight %}