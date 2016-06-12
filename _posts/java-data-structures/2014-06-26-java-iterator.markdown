---
layout: post
status: publish
published: true
title: Java Iterator
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 921
wordpress_url: http://codenuggets.com/?p=921
date: '2014-06-26 17:06:37 -0500'
date_gmt: '2014-06-26 17:06:37 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3417
  author: Java Help | CodeNuggets
  author_email: ''
  author_url: http://codenuggets.com/2014/08/26/java-help/
  date: '2014-08-26 17:29:27 -0500'
  date_gmt: '2014-08-26 17:29:27 -0500'
  content: "[&#8230;] Structures Java equals Method Java Comparable Interface Java
    Comparator Interface Java Iterator Java Date [&#8230;]"
---
In the language of Java, a collection is just a set of objects. A collection may or may not have order depending on how the collection class is implemented. Examples collection are [`List`](http://docs.oracle.com/javase/7/docs/api/java/util/List.html) (ordered), [`Set`](http://docs.oracle.com/javase/7/docs/api/java/util/Set.html) (unordered), and [`Map`](http://docs.oracle.com/javase/7/docs/api/java/util/Map.html) (hashtables).

A collection iterator is an object that takes a collection and provide the methods to go through the elements of the collection, one at a time. For example, the following code contains a `List` collection, `c`, and an iterator, `itr`, that prints out each element.

{% highlight java %}
List<Integer> c = Arrays.asList(1, 2, 3);
Iterator<Integer> itr = c.iterator();

while(itr.hasNext())
    System.out.print(itr.next() + ' ');
{% endhighlight %}

## Iterator Interface

Every collection iterator must implement [`Iterator<E>`](http://docs.oracle.com/javase/7/docs/api/java/util/Iterator.html) interface. This interface only defines 3 methods (behaviors) that all iterators have:

1. `hasNext()`: this method tells the user of the iterator if the collection has more elements to go through.
2. `next()`: if hasNext() returns true, this method gets the next element and advance the internal tracker.
3. `remove()`: this is rarely implemented; usually the body of this is left blank or throws <a href="http://docs.oracle.com/javase/7/docs/api/java/lang/UnsupportedOperationException.html" target="_blank">UnsupportedOperationException</a>.

Note that `Iterator<E>` is a generic interface. This simply mean that it can be an iterator of different types; or the collection is generic.

## Implementing Iterator

From the code above, we see that we can get an iterator for a collection by calling the `iterator()` method on the collection object. The next question, how do we implement an iterator for our own collection?

An iterator is usually implemented by the the author of the collection, and it really is just a class that implements the `Iterator<E>` interface. With that said, iterators are often written as an inner class of the collection class, so that the iterator can have access the internals of the collection. The following code shows a simple collection class using array and an iterator as inner class.

{% highlight java %}
class MyCollection implements Collection {
    private int[] a;

    Iterator<Integer> iterator() { return new MyIterator(a); }

    //Other members of the class here

    /** Iterator class */
    class MyIterator implements Iterator<Integer> {
        int[] a;
        int tracker;

        MyIterator(int[] a) { //Constructor
            this.a = a;
            this.tracker = 0;
        }

        boolean hasNext() { return tracker < a.length; }
        int next() { return tracker++; }
        void remove() { throw new UnsupportedOperationException(); }
    }
}
{% endhighlight %}

The following is the breakdown:

1. Line 9-21 is the iterator class, which has required methods: `hasNext()` line 18, `next()` line 19, and `remove()`line 20.
2. The `iterator()` method (line 4), which returns an instance of our iterator class.

## Iterator Shortcut (For-Each Loop)

We don't have to explicitly call the `iterator()` method to get the iterator from a collection. Java's for-each loop will do all these for us implicitly. The following code does the same as the first code snippet.

{% highlight java %}
List<Integer> c = Arrays.asList(1, 2, 3);
for(int i : c)
    System.out.print(i + ' ');
{% endhighlight %}
This is called for-each loop. And what it does is for each element in collection `c`, the loop runs one time. Each time, the element is assigned to `i`.