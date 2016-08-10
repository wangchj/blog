---
layout: post
title: Reverse Linked List II
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
---

Reverse a linked list from position `m` to `n`, where 1 ≤ m ≤ n ≤ length of list.

Example

```
List             m    n    Result
1->2->3->4->5    2    4    1->4->3->2->5
1->2->3->4->5    1    2    2->1->3->4->5
1->2->3->4->5    1    1    1->2->3->4->5
```

{% highlight java %}
public class Solution {
    
    /**
     * This algorithm is done in 3 steps:
     * 1. Split the linked list into 3 segments: head, body, and tail
     * 2. Reverse the body segment
     * 3. Recombine all 3 segments
     */
    public ListNode reverseBetween(ListNode head, int m , int n) {
        ListNode headEnd = null; // Last node head segment
        ListNode bodyStart = head; // First node body segment
        
        // Find boundary
        for (int i = 1; i < m; i++) {
            headEnd = bodyStart;
            bodyStart = bodyStart.next;
        }
        
        ListNode bodyEnd = head; // Last node of body segment
        ListNode tailStart = head.next; // First node of tail segment
        
        // Find boundary
        for (int i = 1; i < n; i++) {
            bodyEnd = tailStart;
            tailStart = tailStart.next;
        }
        
        if (headEnd != null)
            headEnd.next = null;
        
        bodyEnd.next = null;
        
        ListNode temp = reverse(bodyStart);
        bodyEnd = bodyStart;
        bodyStart = temp;
        
        if (headEnd != null)
            headEnd.next = bodyStart;
        bodyEnd.next = tailStart;
        
        return headEnd == null ? bodyStart : head;
    }
    
    public ListNode reverse(ListNode head) {
        if(head == null || head.next == null)
            return head;
        ListNode res = reverse(head.next);
        ListNode last = head.next;
        head.next = null;
        last.next = head;
        return res;
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