---
layout: post
status: publish
published: true
title: Setup JUnit in jGrasp
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 968
wordpress_url: http://codenuggets.com/?p=968
date: '2014-07-03 16:57:02 -0500'
date_gmt: '2014-07-03 16:57:02 -0500'
categories:
- Programming
- Java
tags: []
comments:
- id: 3294
  author: Virtual Assistant
  author_email: deetyasoft@gmail.com
  author_url: http://www.ivrguru.com
  date: '2014-08-01 06:57:23 -0500'
  date_gmt: '2014-08-01 06:57:23 -0500'
  content: very nice post liked reading it got very effective information thanks for
    sharing details on virtual assistant visit http://www.ivrguru.com for virtual
    assistant
- id: 3525
  author: one
  author_email: email@email.com
  author_url: ''
  date: '2014-09-16 18:53:48 -0500'
  date_gmt: '2014-09-16 18:53:48 -0500'
  content: " ."
---
<a href="http://www.jgrasp.org/" target="_blank">jGrasp</a> is an IDE brewed at Auburn University that offers visualization of coding data structures. It is a teaching tool for programming and data structure course using Java. This article shows how to configure and run JUnit test cases in jGrasp.

## Configuration

Before writing JUnit test cases, we need to configure jGrasp to use JUnit. The following illustrate the steps.

1. Download JUnit from <a href="http://junit.org/" target="_blank">junit.org</a> and save it somewhere e.g. `/home/me/apps`. What you need are `junit.jar` and `hamcrest-core.jar`
2. In jGrasp, click on Tools menu -> JUnit -> Configure
3. For Junit Home, click on Browse and choose where `junit.jar` is stored (see <a href="/wp-content/figures/setup-junit-in-jgrasp/jgrasp-junit-config.png" target="_blank">figure</a>).

4. Click on OK

Now JUnit is configured and we're ready to write unit tests.

## Creating and Running Tests

The easiest way to create a JUnit test file is to open the class (java file) you want to test and click on the Create jUnit Test File button, as shown below. For example, if you have `Selector.java`, clicking Create Test File button will create a test file named `SelectorTest.java`.

<img src="http://codenuggets.com/wp-content/figures/setup-junit-in-jgrasp/jgrasp-test-cmd.png" />

Another way to create tests is to create your own test file. The following is a template of JUnit test file. If you create your own test file, make sure jGrasp knows it's a  test file. To do so you can drag your test file into test file group in the project.

{% highlight java %}
import org.junit.Assert;
import static org.junit.Assert.*;
import org.junit.Before;
import org.junit.Test;

public class SelectorTest {
    /** Called before each test method **/
    @Before public void setUp() {
    }

    /** A simple test method **/
    @Test public void test() {
        Assert.assertEquals("Fail message", 0, 0); //Expected, actual
        Assert.assertTrue("Fail message", 0 == 0);
    }
}
{% endhighlight %}
After you have a test file, you can use the commands listed above to compile, run and debug your tests.