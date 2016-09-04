---
layout: post
title: Rotate Image
categories: lintcode
tags:
- Java
- Algorithm
- Cracking The Coding Interview
- Matrix
---

You are given an `n x n` 2D matrix representing an image. Rotate the image by 90 degrees (clockwise)

Example

```
1  2         3  1
       -->
3  4         4  2
```

The following is an in-place algorithm.

{% highlight java %}
public class Solution {
    public void rotate(int[][] matrix) {
        //The width of the matrix
        int n = matrix.length;
        //i represent concentric rings of the matrix, 0 represent outer-most ring.
        for(int i = 0; i < n / 2; i++)
        {
            for(int j = 0; j < n - 2 * i - 1; j++)
            {
                //Save one of the elments of the ring before rotation.
                int temp = matrix[i][i + j];
                //Rot 1: West col -> North row
                matrix[i][i + j] = matrix[n - 1 - i - j][i];
                //Rot 2: South row -> West col
                matrix[n - 1 - i - j][i] = matrix[n - 1 - i][n - 1 - i - j];
                //Rot 3: East col -> South row
                matrix[n - 1 - i][n - 1 - i - j] = matrix[i + j][n - 1 - i];
                //Rot 4: North row -> East col
                matrix[i + j][n - 1 - i] = temp;
            }
        }
    }
}
{% endhighlight %}