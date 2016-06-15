---
layout: post
title: Maximum Depth of Binary Tree
categories: lintcode
tags:
- Java
- algorithm
- Divide and Conquer
- Recursion
- Binary Tree
- Uber
---

Given a binary tree, find its maximum depth. The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

Example

```
  1
 / \ 
2   3     Max Depth = 4
   / \    1->3->4->6
  4   5
   \
    6
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: An integer.
     */
    public int maxDepth(TreeNode root) {
        if(root == null)
            return 0;
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }
}
{% endhighlight %}