---
layout: post
title: Route Between Two Nodes in Graph
categories: lintcode
tags:
- Java
- Algorithm
- Cracking The Coding Interview
- Depth First Search
- Breadth First Search
---

Given a directed graph, design an algorithm to find out whether there is a route between two nodes.

Example

```
A----->B----->C
 \     |
  \    |
   \   |
    \  v
     ->D----->E

B to E: true
D to C: false
```

{% highlight java %}
public class Solution {
    ArrayList<DirectedGraphNode> graph;
    HashSet<DirectedGraphNode> v;
    public boolean hasRoute(ArrayList<DirectedGraphNode> graph, 
        DirectedGraphNode s, DirectedGraphNode t) {
        this.graph = graph;
        this.v = new HashSet<>();
        return dfs(s, t);
    }
    
    boolean dfs(DirectedGraphNode s, DirectedGraphNode t) {
        if (s.label == t.label)
            return true;
        v.add(s);
        for (DirectedGraphNode neighbor : s.neighbors)
            if (!v.contains(neighbor) && dfs(neighbor, t))
                return true;
        return false;
    }
}
{% endhighlight %}

{% highlight java %}
class DirectedGraphNode {
    int label;
    ArrayList<DirectedGraphNode> neighbors;
    DirectedGraphNode(int x) {
        label = x;
        neighbors = new ArrayList<DirectedGraphNode>();
    }
}
{% endhighlight %}