---
layout: post
title: Remove Duplicates from Sorted List II
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

Example

```
List             Return
1->2->3->3->4    1->2->4
1->1->1->2->3    2->3
```

{% highlight java %}
public class Solution {
    public static ListNode deleteDuplicates(ListNode head) {
        ListNode prev = null, node = head, drop = null;
        
        while (node != null) {
            if ((node.next != null && node.next.val == node.val) ||
                (drop != null && node.val == drop.val)) 
            {
                drop = node;
                
                if (node == head)
                    head = node = node.next;
                else {
                    prev.next = node.next;
                    node = node.next;
                }
            }
            else {
                prev = node;
                node = node.next;
            }
        }
        
        return head;
    }
}
{% endhighlight %}

{% highlight java %}
public class ListNode {
    int val;
    ListNode next;
    ListNode(int x) {
        val = x;
        next = null;
    }
}
{% endhighlight %}