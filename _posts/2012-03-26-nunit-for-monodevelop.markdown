---
layout: post
status: publish
published: true
title: NUnit for MonoDevelop
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 114
wordpress_url: http://codenuggets.com/?p=114
date: '2012-03-26 18:45:12 -0500'
date_gmt: '2012-03-26 18:45:12 -0500'
categories:
- Uncategorized
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ".NET"
- C#
tags: []
comments:
- id: 44
  author: Josiah Sprengeler
  author_email: Auwaerter1273@gmail.com
  author_url: http://www.qdthyzxe.com
  date: '2012-04-04 18:05:15 -0500'
  date_gmt: '2012-04-04 18:05:15 -0500'
  content: I dugg some of you post as I  cerebrated they were  extremely helpful  very
    helpful
- id: 72
  author: Latosha Winham
  author_email: Burbidge45971@yahoo.com
  author_url: http://indiahottrends.com/
  date: '2012-04-07 21:24:22 -0500'
  date_gmt: '2012-04-07 21:24:22 -0500'
  content: What's up, just wanted to mention, I liked this post. It was practical.
    Keep on posting!
- id: 81
  author: Wm Goodmanson
  author_email: 83Hardgrove@yahoo.com
  author_url: http://www.flashbuzz.info/story.php?id=263802
  date: '2012-04-07 21:37:33 -0500'
  date_gmt: '2012-04-07 21:37:33 -0500'
  content: Absolutely indited content material, thank you for selective information.
    "Necessity is the mother of taking chances." by Mark Twain.
- id: 582
  author: lalaa
  author_email: laal@alal.lala
  author_url: ''
  date: '2012-04-18 22:44:14 -0500'
  date_gmt: '2012-04-18 22:44:14 -0500'
  content: "can anyone confirm that nunit is broken in ubuntu 12.04 (beta) atm?\r\nit
    just does not show up in the references window at all for me although i have all
    fairly related packages installed :/"
- id: 583
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2012-04-19 03:52:04 -0500'
  date_gmt: '2012-04-19 03:52:04 -0500'
  content: lalaa which version of 12.04 do you have (desktop or server, 32bit or 64bit)?
- id: 592
  author: lalaa
  author_email: laal@alal.lala
  author_url: ''
  date: '2012-04-21 13:13:44 -0500'
  date_gmt: '2012-04-21 13:13:44 -0500'
  content: "(afaik there is no difference between desktop and server version apart
    from the initial package selection…) 64b desktop (upgraded incrementally since
    9.10 or so).\r\ni have opened a bug on launchpad because i could not solve it
    yet:\r\nhttps://bugs.launchpad.net/ubuntu/+source/monodevelop/+bug/985294"
- id: 600
  author: SuperNugget
  author_email: cjw39@hotmail.com
  author_url: ''
  date: '2012-04-27 17:42:02 -0500'
  date_gmt: '2012-04-27 17:42:02 -0500'
  content: Thanks for the comment and reporting the bug. Hope this will be fix soon.
    I will undoubtedly upgrading to new version of Ubuntu soon.
- id: 5454
  author: jual geotextile harga murah
  author_email: rodrigomullings@gmail.com
  author_url: http://menjual-geotextile-murah.blogspot.com/
  date: '2016-02-05 14:24:07 -0600'
  date_gmt: '2016-02-05 14:24:07 -0600'
  content: "Hi there! Quick question that's entirely off topic.\r\nDo you know how
    to make your site mobile \r\nfriendly? My website looks weird when browsing from
    \r\nmy iphone4. I'm trying to find a template or plugin that might be able to
    resolve this problem.\r\nIf you have any recommendations, please share.\r\nMany
    thanks!"
- id: 5455
  author: harga geotextile murah jakarta
  author_email: tammiellewelyn@t-online.de
  author_url: http://geotextile-murah-jakarta.blogspot.com/
  date: '2016-02-05 19:24:42 -0600'
  date_gmt: '2016-02-05 19:24:42 -0600'
  content: "Quality content is the secret to interest the visitors \r\nto pay a quick
    visit the site, that's what this \r\nwebsite is providing."
---
In the <a href="http://codenuggets.com/2012/03/26/install-monodevelop-on-ubuntu/">previous post</a>, I wrote about installing MonoDevelop on Ubuntu 10.04 LTS. This post will be about installing NUnit integration for MonoDevelop.

I want to do some testing of my project with unit testing. I've search the web and many site (and videos) claim that MonoDevelop has build in unit testing support as well as class templates for NUnit, but I just couldn't find anything in the IDE pertaining unit testing. After more research, I found that I need to install NUnit Plugin for Mono Develop (monodevelop-nunit). The following are the steps.

## Install NUnit Plugin for Mono Develop.

Install the plugin from the software center.

<a href="/images/uploads/2012/03/InstallNUnitPluginForMonoDevelop.png"><img class="size-medium wp-image-116 " title="Install NUnit Plugin for MonoDevelop" src="/images/uploads/2012/03/InstallNUnitPluginForMonoDevelop-300x180.png" alt="Install NUnit Plugin for MonoDevelop" width="300" height="180" /></a> Install NUnit Plugin for MonoDevelop

After installing, MonoDevelop will have an option for Unit Testing under the View menu as well as panels for running and showing results for tests.

<a href="/images/uploads/2012/03/ViewUnitTestingMenu.png"><img class="size-medium wp-image-164 " title="MonoDevelop Unit Testing Menu" src="/images/uploads/2012/03/ViewUnitTestingMenu-300x169.png" alt="MonoDevelop Unit Testing Menu" width="300" height="169" /></a> MonoDevelop Unit Testing Menu

<a href="/images/uploads/2012/03/MonoDevelopUnitTestPanels.png"><img class="size-medium wp-image-165 " title="MonoDevelop Unit Test Panels" src="/images/uploads/2012/03/MonoDevelopUnitTestPanels-300x161.png" alt="MonoDevelop Unit Test Panels" width="300" height="161" /></a> MonoDevelop Unit Test and Result Panels

## Create Test Project

To write unit tests, we need to first create a .NET library project for our test. Though NUnit plugin adds a new solution type to MonoDevelop called "NUnit Assembly Test Collection", I have not yet figured out the intent or how to use this project type; therefore, we'll house our tests in a regular library project.

After the test project has been created, the project needs to reference the **nunit.framework** assembly. Double click on references, go into All tab, and check the nunit.framework. I found that there are two copies of the assembly of same version. I believe one came with Mono and one just install the second time. I haven't found difference between the two copies.

## Writing Unit Tests

After having created a test project, we're ready to write our unit tests. Create a new C# class in our test Project. Our test class will need to use the features in the **NUnit.Framework** namespace, which is defined in the nunit.framework assembly we referenced in the previous section.

In addition, the class need to be embellished with TestFixtureAttribute ([TestFixture]), and test method with TestAttribute ([Test]). The following is one of my test class.

{% highlight c# %}
using System;
using System.Data;
using NUnit.Framework;
using GeoStoreServer;

namespace GeoStoreServerTest
{
    [TestFixture]
    public class WindowSpatialFilterTest
    {

        [Test]
        public void TestPassesFilter()
        {
            SelectionTerm selTerm = new SelectionTerm("?loc");
            WindowSpatialFilter filter = new WindowSpatialFilter(selTerm, 10, 10, 30, 30);
            Assert.IsTrue(filter.PassesFilter(20, 20));
            Assert.IsTrue(filter.PassesFilter(10, 10));
            Assert.IsTrue(filter.PassesFilter(30, 30));
            Assert.IsTrue(filter.PassesFilter(10, 30));

            Assert.IsFalse(filter.PassesFilter(40, 40));
        }

        [Test]
        public void TestFilter()
        {
            SelectionTerm selTerm = new SelectionTerm("?loc");
            WindowSpatialFilter filter = new WindowSpatialFilter(selTerm,
            10, 10, 30, 30);
            DataTable table = new DataTable();
            table.Columns.Add("?loc", typeof(string));
            //DataRow row = table.NewRow();
            table.Rows.Add("\"15 15\"");
            table.Rows.Add ("\"15 40\""); //This should be filtered out
            table.Rows.Add ("\"20 20\"");
            table.Rows.Add ("\"40 40\""); //This should be filtered out
            table.AcceptChanges();
            table = filter.Filter(table);
            Assert.AreEqual(2, table.Rows.Count);
            Assert.AreEqual ("\"15 15\"", table.Rows[0][0].ToString());
        }

    }
}
{% endhighlight %}

## References

1. <a href="http://stackoverflow.com/questions/924239/what-the-best-setup-latest-mono-monodevelop-on-ubuntu-9-04">What the best setup latest Mono + MonoDevelop on Ubuntu 9.04?</a>
2. <a href="http://www.codeproject.com/Articles/34161/Setup-a-Test-Project-with-NUnit-and-MonoDevelop">Setup a Test Project with NUnit and MonoDevelop</a>
