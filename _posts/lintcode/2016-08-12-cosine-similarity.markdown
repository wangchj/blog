---
layout: post
title: Cosine Similarity
categories: lintcode
tags:
- Java
- Algorithm
- Mathematics
---

Cosine similarity is a measure of similarity between two vectors of an inner product space that measures the cosine of the angle between them. The cosine of 0° is 1, and it is less than 1 for any other angle. It is defined as follows:

![cosine similarity equation](https://wikimedia.org/api/rest_v1/media/math/render/svg/a71c4add4abded66efd42b202c76f6a59944a587)

Given two vectors `A` and `B` with the same size, calculate the cosine similarity. Return `2.0000` if cosine similarity is invalid (for example `A = [0]` and `B = [0]`).

Example

```
A            B            Result
[1, 2, 3]    [2, 3, 4]    0.9926
[0]          [0]          2.0000
```

{% highlight java %}
class Solution {
    public double cosineSimilarity(int[] A, int[] B) {
        if (A == null || B == null || A.length == 0  || B.length == 0)
            return 2;
        
        double a = dotProduct(A, B);
        double b = magnitude(A);
        double c = magnitude(B);
        
        if (b == 0.0 || c == 0.0)
            return 2;
            
        return a / (b * c);
    }
    
    int dotProduct(int[] a, int[] b) {
        int res = 0;
        for (int i = 0; i < a.length; i++)
            res += a[i] * b[i];
        return res;
    }
    
    double magnitude(int[] a) {
        int sum = 0;
        for (int i = 0; i < a.length; i++)
            sum += a[i] * a[i];
        return Math.sqrt(sum);
    }
}
{% endhighlight %}