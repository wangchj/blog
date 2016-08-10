---
layout: post
title: Word Ladder
categories: lintcode
tags:
- Java
- Algorithm
- Bread First Search
- LinkedIn
---

Given two words, `start` and `end`, and a dictionary, find the length of shortest transformation sequence from `start` to `end`. Each intermediate word must be in the dictionary and only one letter can be changed at a time. Return `0` if no such sequence.

Example

Given:  
`start = "hit"`  
`end   = "cog"`  
`dict  = ["hot","dot","dog","lot","log"]`

One shortest sequence is `"hit" -> "hot" -> "dot" -> "dog" -> "cog"`, return its length `5`.


{% highlight java %}
public class Solution {
    /**
      * @param start, a string
      * @param end, a string
      * @param dict, a set of string
      * @return an integer
      */
    public int ladderLength(String start, String end, Set<String> dict) {
        Queue<Node> q = new LinkedList<>(); //Queue
        Set<String> v = new HashSet<>();    //Visited words
        dict.add(end);
        q.add(new Node(start, null));
        while (!q.isEmpty()) {
            Node front = q.remove();
            String str = front.str;
            if (str.equals(end))
                return getLength(front);
            //Mutate the current word
            StringBuilder builder = new StringBuilder(str);
            for (int i = 0; i < str.length(); i++) {
                for (char c = 'a'; c <= 'z'; c++) {
                    builder.setCharAt(i, c);
                    String mutant = builder.toString();
                    if (dict.contains(mutant) && !v.contains(mutant)) {
                        q.add(new Node(mutant, front));
                        v.add(mutant);
                        
                    }
                }
                builder.setCharAt(i, str.charAt(i));
            }
        }
        return 0;
    }
    
    /**
     * Gets the length to the front of the linked nodes.
     */
    int getLength(Node node) {
        int res = 0;
        while (node != null) {
            res++;
            node = node.prev;
        }
        return res;
    }
    
    class Node {
        String str;
        Node prev;
        
        Node(String str, Node prev) {
            this.str = str;
            this.prev = prev;
        }
    }
}
{% endhighlight %}