---
layout: post
title: Unique Binary Search Trees
categories: lintcode
tags:
- Java
- Algorithm
- Catalan Number
- Dynamic Programming
---

Given `n`, how many structurally unique BSTs (binary search trees) that store values `1...n`?

Example

```
n = 3  =>  5 unique trees

1           3    3       2      1
 \         /    /       / \      \
  3      2     1       1   3      2
 /      /       \                  \
2      1         2                  3
```

{% highlight java %}
public class Solution {
    HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
    /**
     * @paramn n: An integer
     * @return: An integer
     */
    public int numTrees(int n) {
        if(n == 0 || n == 1)
            return 1;
        if(map.containsKey(n))
            return map.get(n);
            
        int sum = 0;
        
        for(int i = 1; i <= n; i++) {
            sum += numTrees(i - 1) * numTrees(n - i);
        }
        
        map.put(n, sum);
        
        return sum;
    }
}
{% endhighlight %}