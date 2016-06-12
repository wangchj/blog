---
layout: post
status: publish
published: true
title: Delete Node in the Middle of Singly Linked List
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 1573
wordpress_url: http://codenuggets.com/?p=1573
date: '2016-03-20 02:19:12 -0500'
date_gmt: '2016-03-20 02:19:12 -0500'
categories: lintcode
tags:
- Java
- algorithm
- LeetCode
- LintCode
- LintCode easy
- linked list
- Cracking the Coding Interview
comments: []
---
Implement an algorithm to delete a node in the middle of a singly linked list, given only access to that node.

**Example**

Given `1->2->3->4`, and node `3`. return `1->2->4`

## Solution

Since we are only given the reference to a node in the middle of a singly linked list, we cannot just unlink the node we want to remove, as we usually do.

The way to remove this node is to shift all the values after the current node and remove the last node of the list.

A Java implementation follows.

{% highlight java %}
public class Solution {
    /**
     * @param node: the node in the list should be deleted
     * @return: nothing
     */
    public void deleteNode(ListNode node) {
        ListNode prev = null;
        while(node.next != null) {
            node.val = node.next.val;
            prev = node;
            node = node.next;
        }
        
        prev.next = null;
    }
}

/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */
 {% endhighlight %}
