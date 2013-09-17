---
layout: post
title: "Adding Google Analytics to Octopress blog on Github Pages"
date: 2013-09-17 13:22
comments: true
categories: ['TIL','blog customization','Octopress','Google Analytics','Github Pages']
---
I wanted a way to count visitors for my blog. Easy enough, right? Just sign up for a free Google Analytics account, obtain a tracking ID from the account, and add the tracking ID to Octopress config file...right?

Wrong. Maybe I was doing something else incorrectly, but I didn't get things working until I did [what a guy named Stefan Alfbo wrote about](stefanalfbo.github.io/blog/2013/04/17/octopress-google-analytics-github-pages/). I found his blog post via Google, which reminds me that my own blog's Google-powered search doesn't seem to work **:(**.

## Problem solved

Here's the trick for getting Google Analytics working on an Octopress blog hosted on Github: open up the **source/\_includes/google\_analytics.html** file and add...

~~~
// add this line to the series of _gaq pushes already in the code
_gaq.push(['_setDomainName','github.io']);
~~~
{:lang="js"}

## Questions remain

Alfbo recommends putting this new line of code in between the 2 existing `_gaq.push` statements. I'm not sure if the order of the `_gaq` array really matters, but I didn't want to chance it, so I followed his recommendation. However, this left me wondering, "What is the `_gaq` array anyway? How is it used? And why does it need special attention to get it working with Github hosting?"