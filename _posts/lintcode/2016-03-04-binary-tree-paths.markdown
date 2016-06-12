---
layout: post
status: publish
published: true
title: Binary Tree Paths
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1504
wordpress_url: http://codenuggets.com/?p=1504
date: '2016-03-04 04:35:49 -0600'
date_gmt: '2016-03-04 04:35:49 -0600'
categories: lintcode
tags:
- recursion
- algorithm
- LeetCode
- LintCode
- Binary Tree
- Binary Tree Traversal
- Facebook
- Google
- LintCode easy
comments: []
---

Given a binary tree, return all root-to-leaf paths.

**Example**

Given the following binary tree:

```
   1
 /   \
2     3
 \
  5
```

All root-to-leaf paths are:

```
[
  "1->2->5",
  "1->3"
]
```

## Solution Discussion

The following code is a recursive solution to find all paths of a binary tree from the root node to all leaf nodes. The core of the solution and the recursive method is named `getPath()`. For each node in the tree, we call this method once. For each recursive call, we keep track of the current path in a `List` named `path`. We also keep track of all the paths we found in a `List` named `res`.

`getPath()` first adds the current node to the path. Then it recursively calls `getPath()` once for the left child and once for the right child. When a leaf node is reached, utility method `addResult()` is called to add the string representation of the path to the list `res`. Before a recursive returns (backtracking), the last entry of `path` is removed.

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
     * @param root the root of the binary tree
     * @return all root-to-leaf paths
     */
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> res = new ArrayList<String>();
        List<TreeNode> path = new ArrayList<TreeNode>();
        
        getPath(root, path, res);
        
        return res;
    }
    
    public void getPath(TreeNode node, List<TreeNode> path, List<String> res) {
        if(node == null)
            return;
        
        //Add current node to end of path
        path.add(node);
        
        //If a leaf node is reached, add the current path to res.
        if(node.left == null && node.right == null) {
            addResult(path, res);
            path.remove(path.size() - 1);
            return;
        }
        
        //Recursive call for left and right child nodes.
        getPath(node.left, path, res);
        getPath(node.right, path, res);
        
        //Remove the last entry (current node) from the path.
        path.remove(path.size() - 1);
    }
    
    private void addResult(List<TreeNode> path, List<String> res) {
        StringBuilder s = new StringBuilder();
        for(int i = 0; i < path.size(); i++) {
            if(i > 0)
                s.append("->");
            s.append(path.get(i).val);
        }
        res.add(s.toString());
    }
}
{% endhighlight %}