---
layout: post
title: Validate Binary Search Tree
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
- Binary Search Tree
- Recursion
- Divide and Conquer
---

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.
- A single node tree is a BST

Example

```
   2                 3      
  / \               / \
 1   4             1   5
    / \           / \   \  
   3   5         4   2   6

Valid BST       Invalid BST
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: True if the binary tree is BST, or false
     */
    public boolean isValidBST(TreeNode root) {
        return isValidBST(root, Integer.MIN_VALUE, Integer.MAX_VALUE);
    }
    
    public boolean isValidBST(TreeNode root, int min, int max) {
        if(root == null)
            return true;
            
        if(root.val < min || root.val > max)
            return false;
            
        if(root.left == null && root.right == null)
            return true;
            
        if ((root.left != null && root.left.val >= root.val) ||
            (root.right != null && root.right.val <= root.val))
            return false;
        
        return isValidBST(root.left, min, Math.min(max, root.val)) &&
            isValidBST(root.right, Math.max(min, root.val), max);
    }
}
{% endhighlight %}