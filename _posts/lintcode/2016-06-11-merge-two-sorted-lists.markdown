---
layout: post
title: Merge Two Sorted Lists
categories: lintcode
tags:
- Java
- algorithm
- LinkedIn
- Linked List
---

Merge two sorted (ascending) linked lists and return it as a new sorted list. The new sorted list should be made by splicing together the nodes of the two lists and sorted in ascending order.

Example

```
List 1: 1->3->8->11->15->null
List 2: 2->null
Result: 1->2->3->8->11->15->null
```

{% highlight java %}
public class Solution {
    /**
     * @param ListNode l1 is the head of the linked list
     * @param ListNode l2 is the head of the linked list
     * @return: ListNode head of linked list
     */
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null)
            return l2;
        if(l2 == null)
            return l1;
            
        ListNode res = null;
        ListNode end = null;

        while(l1 != null && l2 != null) {
            ListNode next = null;
            if(l1.val < l2.val) {
                next = l1;
                l1 = l1.next;
            }
            else {
                next = l2;
                l2 = l2.next;
            }
            
            //Attach next to res
            if(res == null) {
                res = end = next;
            }
            else {
                end.next = next;
                end = end.next;
            }
        }
        
        if(l1 != null)
            end.next = l1;
        else if(l2 != null)
            end.next = l2;
        
        return res;
    }
}
{% endhighlight %}