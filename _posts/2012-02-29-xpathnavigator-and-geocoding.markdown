---
layout: post
status: publish
published: true
title: XPathNavigator and Geocoding
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 56
wordpress_url: http://codenuggets.com/?p=56
date: '2012-02-29 04:05:23 -0600'
date_gmt: '2012-02-29 04:05:23 -0600'
categories:
- School
- Research
- Semantic Web
- Spatial Function Triple Store Integration
- Programming
- ASP.NET
tags:
- Spatial RDF Data
- web scraping
- web scraper
- XPathNavigator
- Geocoding
comments:
- id: 75
  author: Mohamed Warley
  author_email: 60Festini@yahoo.com
  author_url: http://daddyfresh.com/story.php?id=88555
  date: '2012-04-07 21:37:24 -0500'
  date_gmt: '2012-04-07 21:37:24 -0500'
  content: I like this post, enjoyed this one  appreciate it for posting .
---
For past week I have been working on a web scraper for the spatial semantic web project. I needed some test data sets of places with location attributes (latitude and longitude) to populate our data store and can later be queries with our system. Since spatial data sets are not easy to find, I decided to write a scraper to get some POI data of gas stations in a region from some websites. The data set I obtained are only from research and testing and purposes and no way used commercially.

Once again, since I love .NET platform so much, the scraper is a Windows Form Application written in C# and .NET Framework.

<b>XPathNavigator Class</b><br />
One thing I found very handy is the XPathNavigator class in the System.Xml.XPath namespace of the .NET Framework. The way I use is I load a segment of HTML code into an XmlDocument object and create an XPathNavigator object as an cursor. After having the object, I can traverse the hierarchy of the HTML code. Snippet of code I used in my project:

{% highlight c# %}
string html = GetPageHtml();
XmlDocument xmlDoc = new XmlDocument();
xmlDoc.Load(html);
XPathNavigator cursor = xmlDoc.CreateNavigator();

cursor.MoveToFollowing("a", ""); //Traverse to a descendant <a> tag
string hrefValue = cursor.GetAttribute("href", "") //Get href of <a> tag

cursor.MoveToRoot(); //Move to root node of HTML
cursor.MoveToFollowing("u", ""); //Get a <u> tag
cursor.MoveToFirstChild(); //Move the first child of the <u> tag
{% endhighlight %}

<b>Geocoding</b><br />
Geocoding is the process of translating a street address into latitude and longitude values. After I obtain the gas stations from the website, I'd like to find the coordinates of the gas stations and augment my data set. The following are two geocoding services I used:<br />
- Geocoder.us<br />
- Google Geocoding API: http://code.google.com/apis/maps/documentation/geocoding/

<b>Geocoder.us</b><br />
To obtain lat, lon values from Geocoder.us service, make an HTTP request to http://geocoder.us/service/csv?address=ADDRESS. The following is my Geocoder.us geocoder class:

{% highlight c# %}
address = address.Replace(' ', '+');
string response = null;
using (StreamReader reader = new StreamReader(
    webClient.OpenRead(
    "http://geocoder.us/service/csv?address=" + address)))
    response = reader.ReadToEnd();

if (response.Contains("sorry"))
    return null;

string[] result = new string[2];

Match m = Regex.Match(response, @"([^,]+),([^,]+)");
result[0] = m.Groups[1].Value;
result[1] = m.Groups[2].Value;
return result;
{% endhighlight %}

One thing to note about this service is that many times it is unable to resolve an address and return and error message. For this reason I also use Google geocoder.

<b>Google Geocoding</b><br />
I found that Google's Geocoding almost always be able to resolve an address. Google service does have the limitation of only allowing 2,500 request per day. To use the service, make an HTTP request to http://maps.googleapis.com/maps/api/geocode/output?parameters. The following is my class.

{% highlight c# %}
//Call Google Geocoding service
address = address.Replace(' ', '+');
string url =
    "http://maps.googleapis.com/maps/api/geocode/xml&sensor=false&address=" +
    address;
string xml = null;
using (StreamReader reader = new StreamReader(webClient.OpenRead(url)))
   xml = reader.ReadToEnd();
XmlDocument xmlDoc = new XmlDocument();
xmlDoc.LoadXml(xml);

//Get response status
XmlElement e = (XmlElement)xmlDoc.SelectSingleNode("/GeocodeResponse/status");
string status =  e.InnerText;

if (status == "OK")
{
    //Status "OK". Parse and return result.
    string[] coords ={
        xmlDoc.SelectSingleNode("//location/lat").InnerText,
        xmlDoc.SelectSingleNode("//location/lng").InnerText
    };
    return coords;
}

//...
{% endhighlight %}

Because of the limitation of the Google service, I first use the Geocoder.us service to see if I can resolve an address, if I couldn't then I'd use the Google's service.

