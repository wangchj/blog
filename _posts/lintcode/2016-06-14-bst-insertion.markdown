---
layout: post
title: Binary Search Tree Insertion
categories: lintcode
tags:
- Java
- algorithm
- Binary Search Tree
---

Given a binary search tree and a new tree node, insert the node into the tree. You should keep the tree still be a valid binary search tree. Assume there is no duplicates in the tree.

Example

```
Insert 6

 2               2
 / \            / \
1   4    -->   1   4
   /              / \ 
  3              3   6
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of the binary search tree.
     * @param node: insert this node into the binary search tree
     * @return: The root of the new binary search tree.
     */
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