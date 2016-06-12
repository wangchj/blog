---
title: Convert Sorted Array to Binary Search Tree With Minimal Height
layout: post
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- Cracking The Coding Interview
- Recursion
- Binary Search
- Binary Tree
---

Given a sorted (increasing order) array, Convert it to create a binary tree with minimal height. There may exist multiple valid solutions, return any of them.

Example

Given `[1,2,3,4,5,6,7]`, return

```
     4
   /   \
  2     6
 / \    / \
1   3  5   7
```

The shortest binary tree is balanced. That means that the height of the left and right sub-trees are the same. We begin by divide the array in half and use the middle value as the root. We keep doing this recusviely on each half and the result is a balanced tree.

{% highlight java %}
public class Solution {
    /**
     * @param A: an integer array
     * @return: a tree node
     */
    public TreeNode sortedArrayToBST(int[] A) {  
        if(A == null || A.length == 0)
            return null;
        return sortedArrayToBST(A, 0, A.length - 1);
    }
    
    public TreeNode sortedArrayToBST(int[] a, int left, int right) {
        if(left == right)
            return new TreeNode(a[left]);
        int mid = (right - left) / 2 + left;
        TreeNode node = new TreeNode(a[mid]);
        TreeNode leftNode = mid == left ? null : sortedArrayToBST(a, left, mid - 1);
        TreeNode rightNode = mid == right ? null : sortedArrayToBST(a, mid + 1, right);
        node.left = leftNode;
        node.right = rightNode;
        return node;
    }
}
{% endhighlight %}