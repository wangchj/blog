---
layout: post
title: Insertion Sort List
categories: lintcode
tags:
- Java
- algorithm
---

Sort a linked list using insertion sort.

Example

Given `1->3->2->0->null`, return `0->1->2->3->null`.

{% highlight java %}
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @return: The head of linked list.
     */
    public ListNode insertionSortList(ListNode head) {
        ListNode node = head;
        while(node != null) {
            ListNode drag = head;
            while(drag != node) {
                if(drag.val > node.val) {
                    drag.val ^= node.val;
                    node.val ^= drag.val;
                    drag.val ^= node.val;
                }
                drag = drag.next;
            }
            node = node.next;
        }
        return head;
    }
}
{% endhighlight %}

Check this [YouTube video](https://www.youtube.com/watch?v=_5_v2E0OWVs) that explains how insertion sort works with a linked list.