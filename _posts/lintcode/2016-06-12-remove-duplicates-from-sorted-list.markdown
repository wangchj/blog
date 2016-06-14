---
layout: post
title: Remove Duplicates from Sorted List
categories: lintcode
tags:
- Java
- algorithm
- Linked List
---

Given a sorted linked list, delete all duplicates such that each element appear only once.

Example

```
1->1->2          =>  1->2
1->1->2->3->3->  =>  1->2->3
```

{% highlight java %}
public class Solution {
    /**
     * @param ListNode head is the head of the linked list
     * @return: ListNode head of linked list
     */
    public static ListNode deleteDuplicates(ListNode head) { 
        if(head == null)
            return null;
            
        ListNode i = head;
        ListNode j = head.next;
        
        while(j != null) {
            if(i.val == j.val) {
                i.next = j.next;
                j = j.next;
            }
            else {
                i = j;
                j = j.next;
            }
        }
        return head;
    }  
}
{% endhighlight %}