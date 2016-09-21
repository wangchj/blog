---
layout: post
title: Convert Sorted List to Balanced Binary Search Tree
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Recursion
---

Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced binary search tree.

Example

```
               2
1->2->3  =>   / \
             1   3
```


The following is a simple and naive solution by converting the linked list to a sorted array and convert the sorted array to the binary search tree.

{% highlight java %}
public class Solution {
    public TreeNode sortedListToBST(ListNode head) {  
        if (head == null)
            return null;
        
        int count = 0;
        for (ListNode node = head; node != null; node = node.next)
            count++;
        
        int[] a = new int[count];
        int i = 0;
        for (ListNode node = head; node != null; node = node.next) {
            a[i] = node.val;
            i++;
        }
        
        return sortedArrayToBST(a);
    }
    
    TreeNode sortedArrayToBST(int[] a) {  
        if(a == null || a.length == 0)
            return null;
        return sortedArrayToBST(a, 0, a.length - 1);
    }
    
    TreeNode sortedArrayToBST(int[] a, int left, int right) {
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

{% highlight java %}
public class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

public class TreeNode {
    public int val;
    public TreeNode left, right;
    public TreeNode(int val) {
        this.val = val;
        this.left = this.right = null;
    }
}
{% endhighlight %}