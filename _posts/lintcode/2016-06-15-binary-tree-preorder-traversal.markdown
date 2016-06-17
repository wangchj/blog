---
layout: post
title: Binary Tree Pre-Order Traversal
categories: lintcode
tags:
- Java
- algorithm
- Binary Tree
- Binary Tree Traversal
- Recursion
- Non-recursion
---

Given a binary tree, traverse the tree and output the node values using pre-order traversal. In pre-order traversal, the values of the tree is output in this order:

1. The value of the current node
2. The values in the left sub-tree
3. The values in the right sub-tree

Example

```
    1
   / \
  2   3   =>  [1, 2, 3, 4, 3]
 / \
4   5
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: Preorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> preorderTraversal(TreeNode root) {
        ArrayList<Integer> res = new ArrayList<Integer>();
        traverse(root, res);
        return res;
    }
    
    public void traverse(TreeNode root, ArrayList<Integer> res) {
        if(root == null)
            return;
        res.add(root.val);
        traverse(root.left, res);
        traverse(root.right, res);
    }
}
{% endhighlight %}

Challenge: can you do it without recursion?