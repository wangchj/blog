---
layout: post
title: Invert Binary Tree
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
- Recursion
---

Invert a binary tree so that the left and right children of each node swap.

Example

```
  1         1
 / \       / \
2   3  => 3   2
   /       \
  4         4
```

The following is a recursive algorithm:

{% highlight java %}
public class Solution {
    public void invertBinaryTree(TreeNode root) {
        if(root == null)
            return;
        
        invertBinaryTree(root.left);
        invertBinaryTree(root.right);
        
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;
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