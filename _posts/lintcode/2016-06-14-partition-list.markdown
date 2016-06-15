---
layout: post
title: Partition Linked List
categories: lintcode
tags:
- Java
- algorithm
- Linked List
- Two Pointers
---

Given a linked list and a value `x`, partition it such that all nodes less than `x` come before nodes greater than or equal to `x`. You should preserve the original relative order of the nodes in each of the two partitions.

Example

Given `1->4->3->2->5->2->null` and `x = 3`  
Return `1->2->2->4->3->5->null`

{% highlight java %}
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @param x: an integer
     * @return: a ListNode 
     */
    public ListNode partition(ListNode head, int x) {
        if(head == null)
            return null;
            
        //Get the last node of the list
        ListNode end = head;
        while(end.next != null)
            end = end.next;
        
        if(end == head)
            return head;
            
        ListNode prev = null;
        ListNode curr = head;
        ListNode last = end;
        
        while(curr != null) {
            //If curr.val >= x, move curr to the end of the list
            if(curr.val >= x) {
                if(prev == null) {
                    head = curr.next;
                    curr.next = null;
                    last.next = curr;
                    last = last.next;
                    curr = head;
                }
                else {
                    prev.next = curr.next;
                    curr.next = null;
                    last.next = curr;
                    last = last.next;
                    curr = prev.next;
                }
                
                if(last == end)
                    break;
            }
            else {
                if(curr == end)
                    break;
                    
                prev = curr;
                curr = curr.next;
            }
        }
        return head;
    }
}
{% endhighlight %}