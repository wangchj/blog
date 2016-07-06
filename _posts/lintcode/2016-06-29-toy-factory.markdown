---
layout: post
title: Toy Factory
categories: lintcode
tags:
- Java
- Design Pattern
---

Factory is a design pattern in common usage. Please implement a ToyFactory which can generate proper toy based on the given type.

Example

```
ToyFactory tf = ToyFactory();
Toy toy = tf.getToy('Dog');
toy.talk(); 
>> Wow

toy = tf.getToy('Cat');
toy.talk();
>> Meow
```

{% highlight java %}
interface Toy {
    void talk();
}

class Dog implements Toy {
    public void talk() {
        System.out.println("Wow");
    }
}

class Cat implements Toy {
    public void talk() {
        System.out.println("Meow");
    }
}

public class ToyFactory {
    /**
     * @param type a string
     * @return Get object of the type
     */
    public Toy getToy(String type) {
        switch(type) {
            case "Dog":
                return new Dog();
            case "Cat":
                return new Cat();
            default:
                return null;
        }
    }
}
{% endhighlight %}