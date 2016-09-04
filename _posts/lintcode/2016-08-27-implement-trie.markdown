---
layout: post
title: Implement Trie
categories: lintcode
tags:
- Java
- Algorithm
- Trie
- Facebook
- Uber
- Google
---

Implement a trie with insert, search, and startsWith methods.

Assume that all inputs are consist of lowercase letters a-z.

Example

```
insert("lintcode")
search("code")          // return false
startsWith("lint")      // return true
startsWith("linterror") // return false
insert("linterror")
search("lintcode)       // return true
startsWith("linterror") // return true
```

{% highlight java %}
class TrieNode {
    HashMap<Character, TrieNode> map;
    boolean isWord;
    
    public TrieNode() {
        map = new HashMap<>(); 
        isWord = false;   
    }
}

public class Trie {
    private TrieNode root;

    public Trie() {
        root = new TrieNode();
    }

    // Inserts a word into the trie.
    public void insert(String word) {
        TrieNode node = root;
        for (int i = 0; i < word.length(); i++) {
            char c = word.charAt(i);
            if (node.map.containsKey(c)) {
                node = node.map.get(c);
            }
            else {
                TrieNode n = new TrieNode();
                node.map.put(c, n);
                node = n;
            }
            if (i == word.length() - 1)
                node.isWord = true;
        }
    }

    // Returns if the word is in the trie.
    public boolean search(String word) {
        TrieNode node = root;
        for (int i = 0; i < word.length(); i++) {
            char c = word.charAt(i);
            if (!node.map.containsKey(c))
                return false;
            node = node.map.get(c);
        }
        return node.isWord;
    }

    // Returns if there is any word in the trie
    // that starts with the given prefix.
    public boolean startsWith(String prefix) {
        TrieNode node = root;
        for (int i = 0; i < prefix.length(); i++) {
            char c = prefix.charAt(i);
            if (!node.map.containsKey(c))
                return false;
            node = node.map.get(c);
        }
        return true;
    }
}
{% endhighlight %}