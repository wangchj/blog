---
layout: post
title: Clone Binary Tree
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
---

Given a binary tree, return a deep copy of it.

{% highlight java %}
public class Solution {
    public TreeNode cloneTree(TreeNode root) {
        if (root == null)
            return null;
        
        Queue<TreeNode> origin = new LinkedList<>();
        Queue<TreeNode> clone  = new LinkedList<>();
        
        TreeNode res = new TreeNode(root.val);
        
        origin.add(root);
        clone.add(res);
        
        while (!origin.isEmpty()) {
            TreeNode o = origin.remove();
            TreeNode c = clone.remove();
            
            if (o.left != null) {
                c.left = new TreeNode(o.left.val);
                origin.add(o.left);
                clone.add(c.left);
            }
            
            if (o.right != null) {
                c.right = new TreeNode(o.right.val);
                origin.add(o.right);
                clone.add(c.right);
            }
        }
        
        return res;
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