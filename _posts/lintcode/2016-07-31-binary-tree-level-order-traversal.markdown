---
layout: post
title: Binary Tree Level Order Traversal
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
- Binary Tree Traversal
- Queue
- Breadth First Search
- LinkedIn
- Uber
- Facebook
---

Given a binary tree, partition the value of the nodes by level.

Example

```
Given the following binary tree:

    3
   / \
  9  20
    /  \
   15   7

Return level partitions as:

[
  [3],
  [9,20],
  [15,7]
]
```

{% highlight java %}
public class Solution {
    /**
     * @param root: The root of binary tree.
     * @return: Level order a list of lists of integer
     */
    public ArrayList<ArrayList<Integer>> levelOrder(TreeNode root) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        if (root == null)
            return res;
        Queue<TreeNode> q = new LinkedList<>();
        ArrayList<Integer> list = new ArrayList<>();
        int c1 = 1; // The number of nodes in current level
        int c2 = 0; // The number of nodes below current level
        q.add(root);
        while (!q.isEmpty()) {
            TreeNode node = q.remove();
            list.add(node.val);
            c1--;
            if (node.left != null) {
                c2++;
                q.add(node.left);
            }
            if (node.right != null) {
                c2++;
                q.add(node.right);
            }
            if (c1 == 0) {
                res.add(list);
                c1 = c2;
                c2 = 0;
                list = new ArrayList<>();
            }
        }
        return res;
    }
}
{% endhighlight %}