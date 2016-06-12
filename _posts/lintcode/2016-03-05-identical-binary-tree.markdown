---
layout: post
status: publish
published: true
title: Identical Binary Tree
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1509
wordpress_url: http://codenuggets.com/?p=1509
date: '2016-03-05 03:57:39 -0600'
date_gmt: '2016-03-05 03:57:39 -0600'
categories: lintcode
tags:
- Java
- recursion
- algorithm
- LeetCode
- LintCode
- Binary Tree
- LintCode easy
comments: []
---
Check if two binary trees are identical. Identical means the two binary trees have the same structure and every identical position has the same value.

Examples:

```
    1             1
   / \           / \
  2   2   and   2   2
 /             /
4             4
```
are identical.

```
    1             1
   / \           / \
  2   3   and   2   3
 /               \
4                 4
```
are not identical.

## Solution

This can be easily implemented using a recursive algorithm as shown below. In the algorithm, we first check to see if the root nodes `a` and `b` are the same. We know the tree are not identical if the value of `a` and `b` are not the same. If the current nodes are the same, we recursively check the left child and right child of both trees and the process repeats.

{% highlight java %}
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */
public class Solution {
    /**
     * @param a, b, the root of binary trees.
     * @return true if they are identical, or false.
     */
    public boolean isIdentical(TreeNode a, TreeNode b) {
        if(a == null && b == null)
            return true;
        if((a == null && b != null) || (a != null && b == null) ||
            a.val != b.val)
            return false;
        return isIdentical(a.left, b.left) && isIdentical(a.right, b.right);
    }
}
{% endhighlight %}