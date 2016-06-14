---
layout: post
title: Minimum Depth of Binary Tree
categories: lintcode
tags:
- Java
- algorithm
- Binary Tree
- Depth First Search
- Recursion
---

Given a binary tree, find its minimum depth. The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Example

```
  1
 / \ 
2   3      Minimum depth = 2
   / \
  4   5
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: An integer.
     */
    public int minDepth(TreeNode root) {
        if(root == null)
            return 0;
        if(root.left == null && root.right == null)
            return 1;
        
        if(root.left != null && root.right == null)
            return minDepth(root.left) + 1;
        else if(root.left == null && root.right != null)
            return minDepth(root.right) + 1;
        else
            return Math.min(minDepth(root.left), minDepth(root.right)) + 1;
    }
}
{% endhighlight %}