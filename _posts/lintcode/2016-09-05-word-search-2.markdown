---
layout: post
title: Word Search II
categories: lintcode
tags:
- Java
- Algorithm
- Recursion
- Depth First Search
- Backtracking
- Trie
- Airbnb
---

Given a matrix of lower case letters and a dictionary, find all words in the dictionary that can be found in the matrix. A word can start from any position in the matrix and go left, right, up or down to an adjacent position.

Example

```
h, h, t
o, l, k
m, e, e

Dictionary: {dog, cat, home, hulk}
Return:     {home, hulk}
```

Reusing the depth-first search algorithm from [Word Search](word-search).

{% highlight java %}
public class Solution {
    public ArrayList<String> wordSearchII(char[][] board, 
        ArrayList<String> words)
    {
        ArrayList<String> res = new ArrayList<>();
        
        for (String word : words)
            if (exist(board, word))
                res.add(word);
        
        return res;
    }
    
    boolean exist(char[][] board, String word) {
        Set<Integer> visited = new HashSet<>();
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[0].length; j++) {
                if (dfs(board, word, i, j, 0, visited))
                    return true;
            }
        }
        
        return false;
    }
    
    /**
     * Return true if word is found; false otherwise.
     */
    boolean dfs(char[][] board, String word, int row, int col,
        int p, Set<Integer> visited)
    {
        if (row < 0 || row >= board.length ||
            col < 0 || col >= board[0].length)
            return false;
        
        //If cell already visited, return false
        if (visited.contains(row * board[0].length + col))
            return false;
        
        //If character does not match, return false
        if (board[row][col] != word.charAt(p))
            return false;
        
        //If found, return true
        if (p == word.length() - 1 && board[row][col] == word.charAt(p))
            return true;
        
        //Set current cell as visited    
        visited.add(row * board[0].length + col);
        
        //Recursive search
        if (dfs(board, word, row - 1, col, p + 1, visited))
            return true;
        if (dfs(board, word, row + 1, col, p + 1, visited))
            return true;
        if (dfs(board, word, row, col - 1, p + 1, visited))
            return true;
        if (dfs(board, word, row, col + 1, p + 1, visited))
            return true;
        
        //Set current cell as unvisited before return
        visited.remove(row * board[0].length + col);
        
        return false;
    }
}
{% endhighlight %}