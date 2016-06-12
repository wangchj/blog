---
layout: post
status: publish
published: true
title: Flatten Binary Tree to Linked List
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1528
wordpress_url: http://codenuggets.com/?p=1528
date: '2016-03-07 22:15:12 -0600'
date_gmt: '2016-03-07 22:15:12 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- Binary Tree
- LintCode easy
- depth-first search
comments: []
---

Flatten a binary tree to a fake "linked list" in pre-order traversal.

Here we use the right pointer in TreeNode as the next pointer in ListNode.

Don't forget to mark the left child of each node to `null`. Or you will get Time Limit Exceeded or Memory Limit Exceeded.

**Example**

```
              1
               \
     1          2
    / \          \
   2   5    =>    3
  / \   \          \
 3   4   6          4
                     \
                      5
                       \
                        6
```

## Discussion

This problem can be easily implemented using an recursive algorithm. We first call `flatten()` on the left and right subtrees. The base case of this method would be either when the tree node is null or the node is a leaf node.

Once we have flattened the child subtrees, we can assign the flattened last subtree to be the right subtree. We find the end of the flattened left tree and connect the flattened right subtree to that.

{% highlight java %}
public class Solution {
    /**
     * @param root: a TreeNode, the root of the binary tree
     * @return: nothing
     */
    public void flatten(TreeNode root) {
        if(root == null)
            return;
    
        flatten(root.left);
        flatten(root.right);
        
        if(root.left != null && root.right != null) {
            TreeNode right = root.right;
            root.right = root.left;
            root.left = null;
            
            TreeNode tail = root.right;
            while(tail.right != null)
                tail = tail.right;
            tail.right = right;
        }
        else if(root.left != null && root.right == null) {
            root.right = root.left;
            root.left = null;
        }
    }
}

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
{% endhighlight %}
