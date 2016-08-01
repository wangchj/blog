---
layout: post
title: Search Range in Binary Search Tree
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
- Binary Search Tree
---

Given two values `k1` and `k2` (where `k1 < k2`) and a root pointer to a binary search tree, find all the keys in the tree in range `k1` to `k2`. Return all the keys in ascending order.

Example

Give `k1 = 10`, `k2 = 22` and the following tree, return `[12, 20, 22]`.

```
    20
   /  \
  8   22
 / \
4   12
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of the binary search tree.
     * @param k1 and k2: range k1 to k2.
     * @return: Return all keys that k1<=key<=k2 in ascending order.
     */
    public ArrayList<Integer> searchRange(TreeNode root, int k1, int k2) {
        ArrayList<Integer> res = new ArrayList<>();
        search(root, k1, k2, res);
        return res;
    }
    
    private void search(TreeNode root, int k1, int k2, ArrayList<Integer> res) {
        if (root == null)
            return;
        if (root.val < k1) {
            search(root.right, k1, k2, res);
        }
        else if (root.val > k2) {
            search(root.left, k1, k2, res);
        }
        else {
            search(root.left, k1, k2, res);
            res.add(root.val);
            search(root.right, k1, k2, res);
        }
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