---
layout: post
title: Graph Valid Tree
categories: lintcode
tags:
- Java
- Algorithm
- Union Find
- Facebook
- Google
- Zenefits
---

Given `n` nodes labeled from `0` to `n - 1` and a list of undirected edges (as a pair of nodes), write a function to check whether these edges make up a valid tree. You can assume that no duplicate edges will appear in edges. Since all edges are undirected, `[0, 1]` is the same as `[1, 0]` and thus will not appear together in edges.

Example

Given `n = 5` and `edges = [[0, 1], [0, 2], [0, 3], [1, 4]]`, return `true`.

Given `n = 5` and `edges = [[0, 1], [1, 2], [2, 3], [1, 3], [1, 4]]`, return `false`.


The following uses disjoint sets find and union approach.

{% highlight java %}
public class Solution {
    int[] sets; //Disjoint sets
    
    public boolean validTree(int n, int[][] edges) {
        initSets(n);
        
        int count = n; //The number of disjoint sets
        
        for (int[] edge : edges) {
            int set1 = getSet(edge[0]);
            int set2 = getSet(edge[1]);
            if (set1 == set2)
                return false;
            merge(set1, set2);
            count--;
        }
        
        return count == 1;
    }
    
    void initSets(int n) {
        sets = new int[n];
        for (int i = 0; i < n; i++)
            sets[i] = i;
    }
    
    int getSet(int node) {
        while (sets[node] != node)
            node = sets[node];
        return node;
    }
    
    void merge(int set1, int set2) {
        if (set1 < set2)
            sets[set2] = set1;
        else
            sets[set1] = set2;
    }
}
{% endhighlight %}