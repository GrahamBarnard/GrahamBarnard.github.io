---
layout: post
title:  "Salesforce Date Formatting in Apex"
date:   2016-02-29 12:00:00
categories: Development
banner_image: "/media/city_skyline.jpeg"
featured: true
comments: true
---

Formatting Salesforce dates in Apex is straightforward. The most challenging part is understanding how the date syntax formatting works and that will only take you five minutes to figure out. So why am I writing this blog post? Because I always forget how this works and I'm sick and tired of regoogling this and not finding good Apex specific examples.

<!--more-->

## Useful Salesforce Links

[Datetime Format Methods](https://developer.salesforce.com/docs/atlas.en-us.200.0.apexcode.meta/apexcode/apex_methods_system_datetime.htm#apex_System_Datetime_format){:target="_blank"}  
[Date Format Syntax](http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html){:target="_blank"}

## Datetime to String 

<pre><code class="java">String dateFormat = 'yyyy-MM-dd\'T\'HH:mm:ss\'Z\'';

DateTime dt = DateTime.now();
String dateString = dt.format(dateFormat);
System.debug(dateString); // 2016-02-29T22:30:48Z
</code></pre>

## Date to String 

<pre><code class="java">String dateFormatString = 'yyyy-MM-dd';

Date d = Date.today();
Datetime dt = Datetime.newInstance(d.year(), d.month(),d.day());
String dateString = dt.format(dateFormatString);
System.debug(dateString); // 2016-02-29
</code></pre>


## Useful Examples

<pre><code class="java">
// 2016-02-29
Datetime.now().format('yyyy-MM-dd');

// 2016-02-29T23:50:24Z873
Datetime.now().format('yyyy-MM-dd\'T\'HH:mm:ss\'Z\'SSS');

// 2016.02.29 AD at 23:52:20 EST
Datetime.now().format('yyyy.MM.dd G \'at\' HH:mm:ss z');

// Mon, 29 Feb 2016 23:54:22 -0500
Datetime.now().format('EEE, d MMM yyyy HH:mm:ss Z');

// Today is Monday
Datetime.now().format('\'Today is\' EEEE');

// Tuesday March 01, 2016 is the 61 day of the year
Datetime.now().format('EEEE MMMM dd, YYYY \'is the\' D \'day of the year\'');

// Tuesday March 01, 2016 is the 1 day of the month
Datetime.now().format('EEEE MMMM dd, YYYY \'is the\' d \'day of the month\'');

</code></pre>
