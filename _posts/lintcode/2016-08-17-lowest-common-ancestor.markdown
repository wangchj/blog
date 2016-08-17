---
layout: post
title: Lowest Common Ancestor
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
- Recursion
- Hash Table
- Depth First Search
- LinkedIn
- Facebook
---

Given the root and two nodes in a binary tree. Find the lowest common ancestor(LCA) of the two nodes.

The lowest common ancestor is the node with largest depth which is the ancestor of both nodes.

Note that the binary tree does not have to be a binary search tree. Assume both nodes exist in the tree.

Example

```
  4         LCA(3, 5) = 4
 / \        LCA(5, 6) = 7
3   7       LCA(6, 7) = 7
   / \
  5   6
```

Recursive depth-first search solution:

{% highlight java %}
public class Solution {
    TreeNode res;
    
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode a, TreeNode b) {
        Set<TreeNode> set = new HashSet<>();
        dfs1(root, a, set);
        dfs2(root, b, set);
        return res;
    }
    
    /**
     * Depth-first search that returns true if target found.
     */
    boolean dfs1(TreeNode node, TreeNode target, Set<TreeNode> set) {
        if (node == null)
            return false;
        
        set.add(node);
        if (node.val == target.val) 
            return true;
        
        boolean found = dfs1(node.left, target, set) ||
            dfs1(node.right, target, set);
        if (!found)
            set.remove(node);
        
        return found;
    }
    
    boolean dfs2(TreeNode node, TreeNode target, Set<TreeNode> set) {
        if (node == null)
            return false;
        
        if (node.val == target.val) {
            if (set.contains(node))
                res = node;
            return true;
        }
        
        if (dfs2(node.left, target, set) || dfs2(node.right, target, set)) {
            if (res == null && set.contains(node))
                res = node;
            return true;
        }
        
        return false;
    }
}
{% endhighlight %}