---
layout: post
title: Topological Sorting
categories: lintcode
tags:
- Java
- Algorithm
- Graph
- Breadth First Search
- Depth First Search
---

Given a directed graph, find a topological order of the graph.

A topological order of a graph nodes is defined as follow:

- For each directed edge `A -> B` in graph, node `A` must before node `B` in the order list.
- The first node in the order can be any node in the graph with no nodes direct to it.

Example

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcThE9AgZZszyhwe0o9qpp3VyizdIj9kWwMY50HiQEysXvkSLsoZ">

Two valid topological ordering of the graph are:

```
[0, 1, 2, 3, 4, 5]
[0, 2, 3, 1, 5, 4]
```

{% highlight java %}
public class Solution {
    
    // The result list
    ArrayList<DirectedGraphNode> res = new ArrayList<>();
    
    // A list of nodes that don't have incoming edges and
    // can be added to the result list
    Queue<DirectedGraphNode> q = new LinkedList<>();
    
    // Count of incoming edges of each node
    HashMap<DirectedGraphNode, Integer> count = new HashMap<>();
    
    /**
     * Topological sort
     */
    public ArrayList<DirectedGraphNode> topSort(
        ArrayList<DirectedGraphNode> graph)
    {
        init(graph); // Init queue and count from graph
        
        while (!q.isEmpty()) {
            DirectedGraphNode node = q.remove();
            res.add(node);
            for (DirectedGraphNode neighbor : node.neighbors) {
                if (count.get(neighbor) == 1)
                    q.add(neighbor);
                else
                    count.put(neighbor, count.get(neighbor) - 1);
            }
        }
        
        return res;
    }
    
    void init(ArrayList<DirectedGraphNode> graph) {
        initCountHashMap(graph);
        initQueue();
    }
    
    /**
     * Get the incoming edge count of each node in the input graph
     */
    void initCountHashMap(ArrayList<DirectedGraphNode> graph) {
        for (DirectedGraphNode node : graph) {
            if (!count.containsKey(node))
                count.put(node, 0);
            for (DirectedGraphNode neighbor : node.neighbors) {
                if (count.containsKey(neighbor))
                    count.put(neighbor, count.get(neighbor) + 1);
                else
                    count.put(neighbor, 1);
            }
        }
    }
    
    /**
     * Find all nodes that have in-degree of 0
     */
    void initQueue() {
        for (Map.Entry<DirectedGraphNode, Integer> entry :
            count.entrySet())
        {
            if (entry.getValue() == 0)
                q.add(entry.getKey());
        }
    }
}
{% endhighlight %}