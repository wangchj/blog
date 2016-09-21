---
layout: post
title: Binary Tree Maximum Path Sum
categories: lintcode
tags:
- Java
- Algorithm
- Divide and Conquer
- Recursion
- Dynamic Programming
---

Given a binary tree, find the maximum path sum. The path may start and end at any node in the tree.

Example

```
  1
 / \
2   3

Max Path Sum = 6
```

The following algorithm uses recursion to find vertical maximum path sum, which is the maximum path sum from a node down to its descendant. Then the vertical path sum is used to find cross maximum path sum, which is from child to child.

{% highlight java %}
public class Solution {
    int singleMax = Integer.MIN_VALUE;
    int crossMax = Integer.MIN_VALUE;
    
    public int maxPathSum(TreeNode root) {
        int vertMax = search(root);
        return Math.max(singleMax, Math.max(vertMax, crossMax));
    }
    
    int search(TreeNode node) {
        if (node == null)
            return 0;
        
        int maxLeft = search(node.left);
        int maxRight = search(node.right);
        int cross = node.val + maxLeft + maxRight;
        if (cross > crossMax)
            crossMax = cross;
        if (node.val > singleMax)
            singleMax = node.val;
            
        return node.val + Math.max(maxLeft, maxRight);
    }
}
{% endhighlight %}

{% highlight java %}
public class TreeNode {
    public int val;
    public TreeNode left, right;
    public TreeNode(int val) {
        this.val = val;
        this.left = this.right = null;
    }
}
{% endhighlight %}