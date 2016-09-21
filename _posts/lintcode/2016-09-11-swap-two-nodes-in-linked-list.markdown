---
layout: post
title: Swap Two Nodes in Linked List
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Given a linked list and two values `v1` and `v2`. Swap the two nodes in the linked list with values `v1` and `v2`. It's guaranteed there is no duplicate values in the linked list. If `v1` or `v2` does not exist in the given linked list, do nothing.

You should swap the two nodes with values `v1` and `v2`. Do not directly swap the values of the two nodes.

Example

Given `1->2->3->4->null`, `v1 = 2`, `v2 = 4`, return `1->4->3->2->null`.

{% highlight java %}
public class Solution {
    public ListNode swapNodes(ListNode head, int v1, int v2) {
        if (v1 == v2)
            return head;
            
        ListNode prev1 = null, node1 = null, prev2 = null, node2 = null;
        
        //Search for the first node
        node1 = head;
        while (node1 != null && node1.val != v1) {
            prev1 = node1;
            node1 = node1.next;
        }
        
        //Search for the second node
        node2 = head;
        while (node2 != null && node2.val != v2) {
            prev2 = node2;
            node2 = node2.next;
        }
        
        if (node1 == null || node2 == null)
            return head;
        
        ListNode tail1 = node1.next, tail2 = node2.next;
        
        if (node2 == node1.next) {
            if (prev1 != null)
                prev1.next = node2;
            node2.next = node1;
            node1.next = tail2;
        }
        else if(node1 == node2.next) {
            if (prev2 != null)
                prev2.next = node1;
            node1.next = node2;
            node2.next = tail1;
        }
        else {
            if (prev1 != null)
                prev1.next = node2;
            node2.next = tail1;
            if (prev2 != null)
                prev2.next = node1;
            node1.next = tail2;
        }
        
        if (node1 == head)
            head = node2;
        else if (node2 == head)
            head = node1;
        
        return head;
    }
}
{% endhighlight %}

{% highlight java %}
public class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; }
}
{% endhighlight %}