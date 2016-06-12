---
layout: post
title: Nth to Last Node in List
categories: lintcode
tags:
- Java
- algorithm
- Cracking The Coding interview
- Linked  List
---

Find the nth to last element of a singly linked list. 

The minimum number of nodes in list is n.

Example

Given a List  `3->2->1->5->null` and `n = 2`, return node  whose value is `1`.

{% highlight java %}
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @param n: An integer.
     * @return: Nth to last node of a singly linked list. 
     */
    ListNode nthToLast(ListNode head, int n) {
        ListNode a = head, b = head;
        for(int i = 0; i < n; i++)
            a = a.next;
        while(a != null) {
            a = a.next;
            b = b.next;
        }
        return b;
    }
}
{% endhighlight %}

