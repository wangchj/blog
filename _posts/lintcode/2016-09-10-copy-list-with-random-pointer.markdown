---
layout: post
title: Copy List with Random Pointer
categories: lintcode
tags:
- Java
- Algorithm
- Linked List
- Hash Table
- Uber
---

A linked list is given such that each node contains an additional random pointer which could point to any node in the list or null. Return a deep copy of the list.


The following solution uses a HashMap to keep track of the nodes that has been visitied. The algorithm has 2 lists: list A is the original list to be copied, and List B is the new copy. The algorithm visits List A one node at a time.

{% highlight java %}
public class Solution {
    public RandomListNode copyRandomList(RandomListNode head) {
        HashMap<RandomListNode, RandomListNode> map = new HashMap<>();
        
        RandomListNode aNode = head; //Node pointer for list a
        RandomListNode bHead = null; //Head pointer for list b
        RandomListNode bPrev = null; //Prev pointer for list b
        RandomListNode bNode = null; //Node pointer for list b
        
        while (aNode != null) {
            if (map.containsKey(aNode))
                bNode = map.get(aNode);
            else {
                bNode = new RandomListNode(aNode.label);
                map.put(aNode, bNode);
            }
            
            if (aNode.random != null) {
                if (map.containsKey(aNode.random))
                    bNode.random = map.get(aNode.random);
                else {
                    bNode.random = new RandomListNode(aNode.random.label);
                    map.put(aNode.random, bNode.random);
                }
            }
            
            if (aNode == head)
                bHead = bPrev = bNode;
            else {
                bPrev.next = bNode;
                bPrev = bNode;
            }
            
            aNode = aNode.next;
        }
        
        return bHead;
    }
}
{% endhighlight %}

{% highlight java %}
class RandomListNode {
    int label;
    RandomListNode next, random;
    RandomListNode(int x) { this.label = x; }
}
{% endhighlight %}