---
layout: post
title: Clone Graph
categories: lintcode
tags:
- Java
- Algorithm
- Breadth First Search
- Facebook
---

Clone an undirected graph. Each node in the graph contains a label and a list of its neighbors.

How we serialize an undirected graph:

Nodes are labeled uniquely.

We use `#` as a separator for each node, and `,` as a separator for node label and each neighbor of the node.

As an example, consider the serialized graph `{0,1,2#1,2#2,2}`.

The graph has a total of three nodes, and therefore contains three parts as separated by `#`.

1. First node is labeled as 0. Connect node 0 to both nodes 1 and 2.
2. Second node is labeled as 1. Connect node 1 to node 2.
3. Third node is labeled as 2. Connect node 2 to node 2 (itself), thus forming a self-cycle.

Visually, the graph looks like the following:

```
   1
  / \
 /   \
0 --- 2
     / \
     \_/
```

Example

return a deep copied graph.

{% highlight java %}
public class Solution {
    public UndirectedGraphNode cloneGraph(UndirectedGraphNode node) {
        if(node == null)
            return null;
            
        //A list of nodes already cloned
        HashMap<Integer, UndirectedGraphNode> map = new HashMap<Integer, UndirectedGraphNode>();
        //A list of nodes to be cloned (neighbor to be constructed)
        Queue<UndirectedGraphNode> q = new LinkedList<UndirectedGraphNode>();
        
        //Add the first node
        q.add(node);
        
        while(!q.isEmpty())
        {
            //Get a node from queue to clone and construct neighbor
            UndirectedGraphNode origin = q.remove();
            UndirectedGraphNode clone;
            
            if(map.containsKey(origin.label))
                clone = map.get(origin.label);
            else
            {
                clone = new UndirectedGraphNode(origin.label);
                map.put(origin.label, clone);
            }
            
            for(UndirectedGraphNode neighbor : origin.neighbors)
            {
                if(map.containsKey(neighbor.label))
                {
                    clone.neighbors.add(map.get(neighbor.label));
                }
                else
                {
                    UndirectedGraphNode n = new UndirectedGraphNode(neighbor.label);
                    clone.neighbors.add(n);
                    map.put(neighbor.label, n);
                    q.add(neighbor);
                }
            }
            
        }
        return map.get(node.label);
    }
}
{% endhighlight %}

{% highlight java %}
class UndirectedGraphNode {
    int label;
    ArrayList<UndirectedGraphNode> neighbors;
    UndirectedGraphNode(int x) {
        label = x; 
        neighbors = new ArrayList<UndirectedGraphNode>();
    }
}
{% endhighlight %}