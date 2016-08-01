---
layout: post
title: Unique Binary Search Trees II
categories: lintcode
tags:
- Java
- Algorithm
- Binary Search Tree
- Catalan Number
- Dynamic Programming
- Depth First Search
---

Given `n`, generate all structurally unique BST's (binary search trees) that store values `1...n`.

Example

```
n = 3  =>  generate the following trees:

1           3    3       2      1
 \         /    /       / \      \
  3      2     1       1   3      2
 /      /       \                  \
2      1         2                  3
```

{% highlight java %}
public class Solution {
    /**
     * @paramn n: An integer
     * @return: A list of root
     */
    public List<TreeNode> generateTrees(int n) {
        if(n <= 0) {
            ArrayList<TreeNode> res = new ArrayList<TreeNode>();
            res.add(null);
            return res;
        }
        return generateTrees(1, n);
    }
    
    public List<TreeNode> generateTrees(int start, int end) {
        ArrayList<TreeNode> res = new ArrayList<TreeNode>();
        if(start == end) {
            res.add(new TreeNode(start));
            return res;
        }
        for(int i = start; i <= end; i++) {
            List<TreeNode> left = i == start ? null : generateTrees(start, i - 1);
            List<TreeNode> right = i == end ? null : generateTrees(i + 1, end);
            if(left == null) {
                for(TreeNode node : right) {
                    TreeNode n = new TreeNode(i);
                    n.right = node;
                    res.add(n);
                }
            }
            else if(right == null) {
                for(TreeNode node : left) {
                    TreeNode n = new TreeNode(i);
                    n.left = node;
                    res.add(n);
                }
            }
            else { //Left and right are not null
                for(TreeNode l : left) {
                    for(TreeNode r : right) {
                        TreeNode n = new TreeNode(i);
                        n.left = l;
                        n.right = r;
                        res.add(n);
                    }
                }
            }
        }
        return res;
    }
}
{% endhighlight %}