---
layout: post
title: Binary Tree Serialization
categories: lintcode
tags:
- Java
- Algorithm
- Binary Tree
- Microsoft
- Yahoo
---

Design an algorithm and write code to serialize and deserialize a binary tree. Writing the tree to a file is called 'serialization' and reading back from the file to reconstruct the exact same binary tree is 'deserialization'. Trees are represented in breadth-first order. See [Binary Tree Representation](http://www.lintcode.com/en/help/binary-tree-representation/) for details.

There is no limit of how you deserialize or serialize a binary tree, you only need to make sure you can serialize a binary tree to a string and deserialize this string to the original structure.

Example

```
  3
 / \
9  20      Serialize ->  {3,9,20,#,#,15,7}
  /  \
 15   7
```

{% highlight java %}
import java.util.LinkedList;

public class BinaryTreeSerialization {
    /**
     * This method will be invoked first, you should design your own algorithm 
     * to serialize a binary tree which denote by a root node to a string which
     * can be easily deserialized by your own "deserialize" method later.
     */
    public String serialize(TreeNode root) {
        StringBuilder res = new StringBuilder();
        LinkedList<TreeNode> q = new LinkedList<>();
        if (root != null)
            q.add(root);
        while (!q.isEmpty()) {
            TreeNode node = q.remove();
            if (res.length() != 0)
                res.append(',');
            res.append(node == null ? "#" : node.val);
            if(node != null) {
                q.add(node.left == null ? null : node.left);
                q.add(node.right == null ? null : node.right);
            }
        }
        
        truncate(res);

        res.insert(0, '{');
        res.append('}');
        return res.toString();
    }
    
    /**
     * This method will be invoked second, the argument data is what exactly
     * you serialized at method "serialize", that means the data is not given by
     * system, it's given by your own serialize method. So the format of data is
     * designed by yourself, and deserialize it here as you serialize it in 
     * "serialize" method.
     */
    public TreeNode deserialize(String data) {
        TreeNode root = null;
        String[] tokens = tokenize(data);
        LinkedList<TreeNode> q = new LinkedList<>();
        int i = 0;
        while (i < tokens.length) {
            if (i == 0) {
                root = new TreeNode(Integer.parseInt(tokens[i]));
                q.add(root);
                i++;
            }
            else {
                TreeNode node = q.remove();
                String token1 = tokens[i].trim();
                String token2 = i < tokens.length - 1 ? tokens[i + 1].trim() : null;
                if (!token1.equals("#")) {
                    node.left = new TreeNode(Integer.parseInt(token1));
                    q.add(node.left);
                }
                if (token2 != null && !token2.equals("#")) {
                    node.right = new TreeNode(Integer.parseInt(token2));
                    q.add(node.right);
                }
                i += 2;
            }
        }
        return root;
    }

    /**
     * Remove the curly brackets '{', '}' and tokenize the string data. If data
     * has no item, an empty array is returned.
     */
    private String[] tokenize(String data) {
        data = data.substring(1, data.length() - 1);
        if (data.equals(""))
            return new String[0];
        return data.split(",");
    }

    /**
     * Truncate extra '#' from the serialized string.
     */
    private void truncate(StringBuilder s) {
        if (s.length() == 0)
            return;
        int i = s.length() - 1;
        while (s.charAt(i) == '#' || s.charAt(i) == ',')
            i--;
        s.setLength(i + 1);
    }
}
{% endhighlight %}

{% highlight java %}
public class TreeNode {
    public int val;
    public TreeNode left, right;
    public TreeNode(int val) {
        this.val = val;
        this.left = this.right = null;
    }
 }
{% endhighlight %}