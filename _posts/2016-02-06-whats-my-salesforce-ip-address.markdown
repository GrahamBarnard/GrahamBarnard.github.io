---
layout: post
title:  "What's My Salesforce IP Address?"
date:   2016-02-06 12:00:00
categories: Development
banner_image: "/media/desk.jpg"
featured: true
comments: true
---

IP whitelisting is an effective method to ensure a secure connection to external environments. Salesforce helps by [providing a range of IPs addresses](https://help.salesforce.com/apex/HTViewSolution?id=000003652){:target="_blank"} that can be whitelisted by external system on your region.  When connecting to an external system, Salesforce recommends whitelisting the entire set of IP ranges.

<!--more-->

Runs this Apex code from Execute Anynomous to find your current IP adresss. 

NOTE: This will only work when you add [https://api.ipify.org](https://api.ipify.org){:target="_blank"} to your remote site settings.

## The Code

 <pre>
String url = 'https://api.ipify.org';

// Pass in the endpoint to be used using the string url
Http h = new Http();
HttpRequest req = new HttpRequest();
req.setEndpoint(url);
req.setMethod('GET');

// Send the request,
HttpResponse res = h.send(req);
String responseBody = res.getBody();

System.debug('Current Ip Address: ' + responseBody);
 </pre>

This code might help troubleshoot an issue, but you cannot guarantee that this will always be your IP address as Salesforce might randomly change it.