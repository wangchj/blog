---
layout: post
title: Insert Node in a Binary Search Tree
categories: lintcode
tags:
- Java
- Algorithm
- Binary Search Tree
- Recursion
---

Given a binary search tree and a new tree node, insert the node into the tree. You should keep the tree still be a valid binary search tree.

Assume that there are no duplicate values.

Example

```
Insert 6:

  2             2
 / \           / \
1   4   -->   1   4
   /             / \ 
  3             3   6
```

Recursive solution:

{% highlight java %}
class Solution {
public class Solution {
    public TreeNode insertNode(TreeNode root, TreeNode node) {
        if(root == null)
            return node;
            
        if(node.val < root.val) {
            if(root.left == null)
                root.left = node;
            else
                insertNode(root.left, node);
        }
        else {
            if(root.right == null)
                root.right = node;
            else
                insertNode(root.right, node);
        }
        return root;
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