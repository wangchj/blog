---
layout: post
title: Remove Nth Node From End of List
categories: lintcode
tags:
- Java
- algorithm
- Linked List
comments: []
---

Given a linked list, remove the nth node from the end of list and return its head.

Example

Given linked list: `1->2->3->4->5->null`, and `n = 2`.

After removing the second node from the end, the linked list becomes `1->2->3->5->null`.

There are two approaches we can use to solve this problem:

1. Count length: we first count the length of the linked list, then on a second pass, we know which node to remove. This approach requires two passes.
2. Two pointers: this approach requires only one pass of the list. We use two node pointers, `a` and `b`, where `a` is `n` nodes ahead of `b`. We then advance both `a` and `b` at the same speed. When `a` reaches the end of the list, `b` is the node to be removed.

Two-Pointer Approach:

{% highlight java %}
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @param n: An integer.
     * @return: The head of linked list.
     */
    ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode adv = head;
        
        // Advance adv node by n
        for (int i = 0; i < n; i++)
            adv = adv.next;
            
        ListNode prev = null;
        ListNode curr = head;
        
        // Advance adv and curr at the same speed
        while (adv != null) {
            adv = adv.next;
            prev = curr;
            curr = curr.next;
        }
        
        // Last step, remove the node
        if (prev == null)
            head = head.next;
        else {
            prev.next = curr.next;
            curr.next = null;
        }
        
        return head;
    }
}
{% endhighlight %}

Length counting approach:

{% highlight java %}
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @param n: An integer.
     * @return: The head of linked list.
     */
    ListNode removeNthFromEnd(ListNode head, int n) {
        int count = count(head);
        ListNode node = head;
        ListNode prev = null;
        
        //If there is only one node
        if(count == 1 && n == 1)
            return null;
        //If removing head
        if(count == n)
            return head.next;
            
        //Get to the node to be removed
        for(int i = 1; i < count - (n - 1); i++) {
            prev = node;
            node = node.next;
        }
        
        //Remove node
        prev.next = node.next;
        node.next = null;
        
        return head;
    }
    
    int count(ListNode head) {
        int count = 0;
        while(head != null) {
            count++;
            head = head.next;
        }
        return count;
    }
}
{% endhighlight %}