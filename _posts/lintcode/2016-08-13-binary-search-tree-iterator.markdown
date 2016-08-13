---
layout: post
title: Binary Search Tree Iterator
categories: lintcode
tags:
- Java
- Algorithm
- Binary Search Tree
- Non-recursion
- Google
- LinkedIn
- Facebook
---

Design an iterator over a binary search tree with the following rules:

- Elements are visited in ascending order (i.e. an in-order traversal)
- `next()` and `hasNext()` queries run in O(1) time in average.

Example

For the following binary search tree, in-order traversal by using iterator is `[1, 6, 10, 11, 12]`

```
  10
 /  \
1    11
 \    \
  6    12
```

O(n) space, O(1) has next and next:

{% highlight java %}
public class BSTIterator {
    LinkedList<TreeNode> list;
    
    public BSTIterator(TreeNode root) {
        list = new LinkedList<>();
        inorder(root);
    }

    void inorder(TreeNode node) {
        if (node == null)
            return;
        inorder(node.left);
        list.add(node);
        inorder(node.right);
    }
    
    //@return: True if there has next node, or false
    public boolean hasNext() {
        return !list.isEmpty();
    }
    
    //@return: return next node
    public TreeNode next() {
        return list.remove();
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