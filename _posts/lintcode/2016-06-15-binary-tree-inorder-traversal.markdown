---
layout: post
title: Binary Tree In-Order Traversal
categories: lintcode
tags:
- Java
- algorithm
- Binary Tree
- Binary Tree Traversal
- Recursion
---

Given a binary tree, traverse the tree and output the node values using in-order traversal. In in-order traversal, the values of the tree is output in this order:

1. The values in the left sub-tree
2. The value of the current node
3. The values in the right sub-tree

Example

```
    1
   / \
  2   3   =>  [4, 2, 5, 1, 3]
 / \
4   5
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: Inorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> inorderTraversal(TreeNode root) {
        ArrayList<Integer> res = new ArrayList<Integer>();
        traverse(root, res);
        return res;
    }
    
    public void traverse(TreeNode root, ArrayList<Integer> res) {
        if(root == null)
            return;
        traverse(root.left, res);
        res.add(root.val);
        traverse(root.right, res);
    }
}
{% endhighlight %}

Challenge: can you do it without recursion?