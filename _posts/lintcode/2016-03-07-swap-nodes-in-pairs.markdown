---
layout: post
status: publish
published: true
title: Swap Nodes in Pairs
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1524
wordpress_url: http://codenuggets.com/?p=1524
date: '2016-03-07 22:06:17 -0600'
date_gmt: '2016-03-07 22:06:17 -0600'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- linked list
comments: []
---
Given a linked list, swap every two adjacent nodes and return its head.

For example, given `1->2->3->4`, you should return the list as `2->1->4->3`.

## Solution

This is a simple pointer manipulation problem. We can use the following list pointers:

1. `a`: the first of two nodes to be swapped at each iteration.
2. `b`: the second of two nodes to be swapped at each iteration
3. `p`: the node before `a` at each iteration
4. `tail`: the remaining nodes of the list, to be swapped in the future iteration

{% highlight java %}
public class Solution {
    /**
     * @param head a ListNode
     * @return a ListNode
     */
    public ListNode swapPairs(ListNode head) {
        if(head == null || head.next == null)
            return head;
        
        //The first of two nodes to be swapped
        ListNode a = head;
        //The second of two nodes to be swapped
        ListNode b = head.next;
        //The node before a. This is also the last node of swapped portion of the list
        ListNode p = null;

        while(true) {
            //The unswapped (future) portion of the list
            ListNode tail = b.next;
            b.next = a;
            a.next = tail;
            
            //Connect already swapped portion to the just swapped nodes
            if(p != null)
                p.next = b;
            
            p = a;
            
            if(a == head)
                head = b;
                
            a = tail;
            if(a == null || a.next == null)
                break;
            b = a.next;
        }
        return head;
    }
}

/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
 {% endhighlight %}
