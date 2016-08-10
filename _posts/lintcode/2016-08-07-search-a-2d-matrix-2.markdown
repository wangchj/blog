---
layout: post
title: Search a 2D Matrix II
categories: lintcode
tags:
- Java
- Algorithm
- Matrix
- Sorted Matrix
- Google
---

Write an efficient algorithm that searches for a value in an `m x n` matrix, and return the number of occurrances of the target.

This matrix has the following properties:

- Integers in each row are sorted from left to right.
- Integers in each column are sorted from up to bottom.
- No duplicate integers in each row or column.

Example

```
[
  [1, 3, 5, 7],
  [2, 4, 7, 8],
  [3, 5, 9, 10]
]

target = 3, return 2
target = 4, return 1
```

{% highlight java %}
public class Solution {
    public int searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0)
            return 0;
            
        int res = 0, w = matrix[0].length;
        
        for (int i = 0; i < matrix.length && w > 0; i++) {
            //Perform binary search
            int left = 0;
            int right = w - 1;
            while (left <= right) {
                int mid = (right - left) / 2 + left;
                int val = matrix[i][mid];
                if (val == target) {
                    res++;
                    w = mid;
                    break;
                }
                else if (val < target) {
                    left = mid + 1;
                }
                else if (val > target) {
                    right = mid - 1;
                }
            }
        }
        
        return res;
    }
}
{% endhighlight %}