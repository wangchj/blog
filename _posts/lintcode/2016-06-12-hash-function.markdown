---
layout: post
title: Hash Function
categories: lintcode
tags:
- Java
- algorithm
- Hash Table
---

In data structure Hash, hash function is used to convert a string(or any other type) into an integer smaller than hash size and bigger or equal to zero. The objective of designing a hash function is to "hash" the key as unreasonable as possible. A good hash function can avoid collision as less as possible. A widely used hash function algorithm is using a magic number 33, consider any string as a 33 based big integer like follow:

```
hashcode("abcd")
    = (ascii(a) * 333 + ascii(b) * 332 + ascii(c) *33 + ascii(d)) % HASH_SIZE 
    = (97* 333 + 98 * 332 + 99 * 33 +100) % HASH_SIZE
    = 3595978 % HASH_SIZE
```

Clarification

For this problem, you are not necessary to design your own hash algorithm or consider any collision issue, you just need to implement the algorithm as described.

Example

For `key = "abcd"` and `size = 100`, return `78`

{% highlight java %}
class Solution {
    /**
     * @param key: A String you should hash
     * @param HASH_SIZE: An integer
     * @return an integer
     */
    public int hashCode(char[] key,int HASH_SIZE) {
        long res = 0;
        long pow = 1;
        for(int i = 0; i < key.length; i++) {
            char c = key[key.length - 1 - i];
            res += (c  * pow) % HASH_SIZE;
            pow = (pow * 33) % HASH_SIZE;
        }
        return (int)(res % HASH_SIZE);
    }
}
{% endhighlight %}