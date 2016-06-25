---
layout: post
title: Search a 2D Matrix
categories: lintcode
tags:
- Java
- Algorithm
- Binary Search
- Matrix
---

Write an efficient algorithm that searches for a value in an `m x n` matrix. If the target value is in the matrix, return `true`; otherwise, return `false`. 

This matrix has the following properties:

- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

The algorithm should have `O(log(n) + log(m))` running time complexity.

Example

```
[
    [1, 3, 5, 7],
    [10, 11, 16, 20],
    [23, 30, 34, 50]
]

target = 3  =>  true
target = 2  =>  false
```

{% highlight java %}
public class Solution {
    /**
     * @param matrix, a list of lists of integers
     * @param target, an integer
     * @return a boolean, indicate whether matrix contains target
     */
    public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix == null || matrix.length == 0)
            return false;
        int[] row = null;
        
        //Search row using binary search
        int left = 0;
        int right = matrix.length - 1;
        
        while(left <= right) {
            int mid = (right - left) / 2 + left;
            
            int[] curr = matrix[mid];
            
            if(curr[0] <= target && curr[curr.length - 1] >= target) {
                row = curr;
                break;
            }
            else if(target < curr[0])
                right = mid - 1;
            else //target > current[last]
                left = mid + 1;
        }
        
        //If row is still null, then no row found; so just return false
        if(row == null)
            return false;
            
        //Search within row using binary search
        left = 0;
        right = row.length - 1;
        
        while(left <= right) {
            int mid = (right - left) / 2 + left;
            if(row[mid] == target)
                return true;
            else if(row[mid] < target)
                left = mid + 1;
            else
                right = mid - 1;
        }
        
        return false;
    }
}
{% endhighlight %}