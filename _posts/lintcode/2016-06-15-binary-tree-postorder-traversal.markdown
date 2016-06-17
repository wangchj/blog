---
layout: post
title: Binary Tree Post-Order Traversal
categories: lintcode
tags:
- Java
- algorithm
- Binary Tree
- Binary Tree Traversal
- Recursion
---

Given a binary tree, traverse the tree and output the node values using post-order traversal. In post-order traversal, the values of the tree is output in this order:

1. The values in the left sub-tree
2. The values in the right sub-tree
3. The value of the current node

Example

```
    1
   / \
  2   3   =>  [4, 5, 2, 3, 1]
 / \
4   5
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: Postorder in ArrayList which contains node values.
     */
    public ArrayList<Integer> postorderTraversal(TreeNode root) {
        ArrayList<Integer> res = new ArrayList<Integer>();
        traverse(root, res);
        return res;
    }
    
    public void traverse(TreeNode root, ArrayList<Integer> res) {
        if(root == null)
            return;
        traverse(root.left, res);
        traverse(root.right, res);
        res.add(root.val);
    }
}
{% endhighlight %}

Challenge: can you do it without recursion?