---
layout: post
title:  "Mocking External Objects"
date:   2016-02-08 12:00:00
categories: Development
banner_image: "/media/parchment.jpeg"
featured: true
comments: true
---

I recently had to an opportunity to work with Salesforce's External Objects to make a pretty sleek and simple integration.  There was a lot of positives working with External Objects especially once you get the initial connection working.  One of my main complaints is the difficulty of properly unit test due to the inability to mock the external object API calls.

<!--more-->

I did manage to work around the issue, but it isn't an actual solution, it's only temporary workaround.  The real solution will come one of the Salesforce releases when they allow support for External Object mocks.

## The Design

This design of this workaround is based on how Salesforce handles [mocking SOSL queries in Salesforce](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_testing_SOSL.htm){:target="_blank"}.  Salesforce has the nifty method Test.setFixedSearchResults(List<Id> ids) which will automatically return the provded sObjects in your next SOSL call. This method was added by Salesforce to allow for predictable behavior when using SOSL queries.  As annoying as methods like these might seem, it's highly appreciated not to have random unit tests failing when pushing to production due to Salesforce inconsistencies.

## Encapsulating the External Calls

To implement this type of design for external objects, it was important to encapsulate the External Object queries to a single class and avoid reimplemeting the same solution everytime we want to call the external object.  


## Version #1

<pre><code class="java">
/**
 *  @description Handles all the External Request queries
 *  @author 	 Graham Barnard
 *  @date        2016-02-08
 */
public with sharing class ExternalRequestModel {
	/**
	 *  @description Find a single request by id
	 *  @author      Graham Barnard
	 *  @date        2016-02-08
	 */
	public static Request__x findById(Id requestId) {
		List&lt;Request__x&gt; requests = [
		    SELECT  Id, Description__c, Type__c
		    FROM Request__x
		    WHERE Id =: requestId
		];

		return (requests.size() > 0) ? requests[0] : null;
	}
}
</code></pre>

I've now created a simple class for all External Request queries and will add the mocking functionality solely to this class. This avoids infecting your whole codebase with sporadic uses of methods like <b>Test.isRunningTest()</b>.

## Version #2

<pre><code class="java">
/**
 *  @description Handles all the External Request queries
 *  @author      Graham Barnard
 *  @date        2016-02-08
 */
public with sharing class ExternalRequestModel {

	public static List&lt;Request__x&gt; mockedRequests = new List&lt;Request__x&gt;();

	/**
	 *  @description Find a single request by id
	 *  @author 	 Graham Barnard
	 *  @date        2016-02-08
	 */
	public static Request__x findById(Id requestId) {
		if(Test.isRunningTest()) {
			return (mockedRequests.size() > 0) ? mockedRequests[0] : null;
		}

		List&lt;Request__x&gt; requests = [
		    SELECT  Id, Description__c, Type__c
		    FROM Request__x
		    WHERE Id =: requestId
		];

		return (requests.size() > 0) ? requests[0] : null;
	}


}
</code></pre>

This version shows the basis of the workaround,. Instead of actually querying the external system, I return the first element of the mocked request.  This will cause code coverage issues, but that's why it's a workaround.  I don't like having a public variable solely for unit tests, so let's try to fix that.

## Version #3

<pre><code class="java">
/**
 *  @description Handles all the External Request queries
 *  @author      Graham Barnard
 *  @date        2016-02-08
 */
public with sharing class ExternalRequestModel {

	@TestVisible private static List&lt;Request__x&gt; mockedRequests = new List&lt;Request__x&gt;();

	/**
	 *  @description Find a single request by id
	 *  @author 	 Graham Barnard
	 *  @date        2016-02-08
	 */
	public static Request__x findById(Id requestId) {
		if(Test.isRunningTest()) {
			return (mockedRequests.size() > 0) ? mockedRequests[0] : null;
		}

		List&lt;Request__x&gt; requests = [
		    SELECT  Id, Description__c, Type__c
		    FROM Request__x
		    WHERE Id =: requestId
		];

		return (requests.size() > 0) ? requests[0] : null;
	}
}
</code></pre>


Yes I finally found a semi useful implementation of @TestVisible!!! This private list is now only available when running tests and won't accidentaly be used by other developers.

Let's look at an example unit test

<pre><code class="java">
/**
 *  @description Sample Request Unit Test
 *  @author 	 Graham Barnard
 *  @date        2016-02-08
 */
@isTest
private class ExternalRequestTest {
	Test.startTest();
	Request__x mockedRequest = new Request__x(
		Description__c='Test Description',
		Type__c='Test Type'
	);

	ExternalRequestModel.mockedRequests.add(mockedRequest);
	Request__x request = ExternalRequestModel.findById(mockedRequest.Id);
	Test.stopTest();

	System.assertEquals('Test Description', request.Description__c);
	System.assertEquals('Test Type', request.Type__c);
}
</code></pre>


## Updated: Version #4

I've had a lot of feedback about code coverage for the model file. This version will improve code coverage, but i prefer the other versions stylistically.

<pre><code class="java">
/**
 *  @description Handles all the External Request queries
 *  @author      Graham Barnard
 *  @date        2016-11-11
 */
public with sharing class ExternalRequestModel {

	@TestVisible private static List&lt;Request__x&gt; mockedRequests = new List&lt;Request__x&gt;();

	/**
	 *  @description Find a single request by id
	 *  @author 	 Graham Barnard
	 *  @date        2016-02-08
	 */
	public static Request__x findById(Id requestId) {
		List&lt;Request__x&gt; requests = (!mockedRequests.isEmpty()) ? mockedRequests : [
		    SELECT  Id, Description__c, Type__c
		    FROM Request__x
		    WHERE Id =: requestId
		];

		return (requests.size() > 0) ? requests[0] : null;
	}
}
</code></pre>

I'd love to hear feedback
