---
layout: post
title:  "Running Code Reviews - A Beginner’s Guide"
date:   2015-10-25 12:00:00
categories: Development
banner_image: "/media/river.png"
featured: true
comments: true
---

When I joined Traction on Demand last year I was looking to take on more responsibility.  The company had recently started an initiative to run a daily developer support hour.  This hour is allocated to having a senior developer available in a meeting room so that any developer on the team can drop by and discuss their current work problems, get a code review or talk about anything going on in their personal life. At this point in my career I had a limited amount of experience running code reviews and I was excited about the opportunity to give to my new team.

<!--more-->

In the next year, I learned a lot of important lessons about how to run a proper code review, and now know what it takes to run a successful session. Here are some guidelines I’ve established from my experience.

## Use source control and a code review tool

Before my company standardized our developer tools, we had a couple of small projects running without any sort of source control. I attempted to code review one of these project in a code editor, and quickly realized that it was a pointless exercise.

Source control and a review tool like BitBucket and GitHub are essential for running a proper code review section.  The ability to clearly identify a developer’s changes is quintessential to understanding his choices and to catch missed opportunities.

## Be respectful

Every code review session starts with a statement similar to these:

* This code kinda sucks
* This code isn’t my best
* This code was written in a hurry to meet deadlines
* I haven’t had time to review this code

While that might be true, I think it’s due to the intimidation factor of the process. It’s intimidating to have someone look over your work. I feel the same way every time I publish one of these “unexceptional" blog posts.

It’s important to remember that the code that you’ll be looking at was laboured over for hours on end and the developer put a lot of mental effort into making sure that it works properly.  We all make mistakes and we all get super fancy when we don’t need to be, but it’s important that the developer knows that it’s fine to make mistakes.  Don’t stifle the growth of your developer by concentrating on trivial errors and making him feel bad. You want repeat customers.

## Always write comments

Even though you're sitting next to the developer going into details about a specific line of code, you still need to write comments for that line. This helps the developer remember your conversation and take action after the session.

## Review small portions of code

It’s impossible to look over a large amount of code in a one sitting.  Large amounts of code can be overwhelming and result in you brushing over classes without actually understanding what’s going on. Pick a small portion of code so you can focus on the details and really understand the reasoning.

## Adjust your comments to their abilities

From session to session you will get developers who are at different stages of their career. Look over the code,identify their strengths and weaknesses and adapt the session to try to get them to the next level. If it’s a junior developer, you will need to concentrate on the bigger issues and brush over some of the smaller ones.

## Have short code review sessions

It takes a lot of concentration to look at someone’s code.  I start to feel tired after 30-45 minutes. If you’re starting to feel worn down, determine a good place to stop and set up a second session to continue.

## Use a checklist

By using code review checklist, I ensure that I don't miss any areas that I deem important.

I started with this checklist and customized it to our coding Standard and added Salesforce specifi items. https://www.liberty.edu/media/1414/%5B6401%5Dcode_review_checklist.pdf

Sample Salesforce Checklist items:

* Are all Trigger code bulkified?
* Are all Trigger code on object centralized to avoid redundant SOQL queries?
* Are all SOQL queries outside of FOR loops?
* Are all DML operations outside of FOR loops?
* Are SOQL queries streamlined and FOR loops optimized?

## Don’t forget to code review tests

I secretly love writing a good suite of tests, but a lot of developers can’t stand it. It’s important to review their tests and make sure they are not superficial. I’m more lenient with code redundancy and structure in tests, but tough on test method naming, verifying that the majority of possible test scenarios are covered and the asserts are detailed.

## Make sure they feel safe

Code review is a tool to help developers accelerate their learning process. It is not a managerial tool to judge or grade your developers. Make sure that you have a good company culture to foster code reviews and your participants feel secure.

## Follow up

When the session is complete the developer should leave with some refactoring to make. Follow up and review their changes, if an additional session is needed, book one. Followups will allow to catch misinterpretations, and it’s always nice to see their progress.