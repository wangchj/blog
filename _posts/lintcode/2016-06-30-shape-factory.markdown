---
layout: post
title: Shape Factory
categories: lintcode
tags:
- Java
- Design Pattern
- OO Design
---

Factory is a design pattern in common usage. Implement a ShapeFactory that can generate correct shape. You can assume that we have only tree different shapes: Triangle, Square and Rectangle.

Example

```
ShapeFactory sf = new ShapeFactory();
Shape shape = sf.getShape("Square");
shape.draw();
>>  ----
>> |    |
>> |    |
>>  ----

shape = sf.getShape("Triangle");
shape.draw();
>>   /\
>>  /  \
>> /____\

shape = sf.getShape("Rectangle");
shape.draw();
>>  ----
>> |    |
>>  ----
```

{% highlight java %}
/**
 * Your object will be instantiated and called as such:
 * ShapeFactory sf = new ShapeFactory();
 * Shape shape = sf.getShape(shapeType);
 * shape.draw();
 */
interface Shape {
    void draw();
}

class Rectangle implements Shape {
    public void draw() {
        System.out.println(" ----");
        System.out.println("|    |");
        System.out.println(" ----");
    }
}

class Square implements Shape {
    public void draw() {
        System.out.println(" ----");
        System.out.println("|    |");
        System.out.println("|    |");
        System.out.println(" ----");
    }
}

class Triangle implements Shape {
    public void draw() {
        System.out.println("  /\\");
        System.out.println(" /  \\");
        System.out.println("/____\\");
    }
}

public class ShapeFactory {
    /**
     * @param shapeType a string
     * @return Get object of type Shape
     */
    public Shape getShape(String shapeType) {
        switch(shapeType) {
            case "Triangle":
                return new Triangle();
            case "Square":
                return new Square();
            case "Rectangle":
                return new Rectangle();
            default:
                return null;
        }
    }
}
{% endhighlight %}