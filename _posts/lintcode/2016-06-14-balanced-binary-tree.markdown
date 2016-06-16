---
layout: post
title: Balanced Binary Tree
categories: lintcode
tags:
- Java
- algorithm
- Binary Search
- Divide and Conquer
- Recursion
---

Given a binary tree, determine if it is height-balanced. For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

Example

```
  3                      3 
 / \                      \
9  20    balanced         20    not balanced
  /  \                   /  \
 15   7                 15   7
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: True if this Binary tree is Balanced, or false.
     */
    public boolean isBalanced(TreeNode root) {
        if (root == null)
            return true;
        if (!isBalanced(root.left) || !isBalanced(root.right))
            return false;
        int hl = getHeight(root.left);
        int hr = getHeight(root.right);
        return (Math.max(hl, hr) - Math.min(hl, hr)) <= 1;
    }
    
    public int getHeight(TreeNode root) {
        if (root == null)
            return 0;
        return Math.max(getHeight(root.left), getHeight(root.right)) + 1;
    }
}
{% endhighlight %}