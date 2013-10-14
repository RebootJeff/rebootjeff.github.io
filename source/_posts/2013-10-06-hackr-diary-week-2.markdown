---
layout: post
title: "[HackR Diary] Week 2: Now Exiting My Comfort Zone"
date: 2013-10-06 22:17
comments: true
categories: ['HackR Diary','Hack Reactor','coding bootcamps']
---

<p class="last-updated">Last updated on Oct 13, 2013 to fix a typo and embedded a tweet.</p>

<blockquote class="twitter-tweet"><p>Awesome of the <a href="https://twitter.com/Airbnb">@Airbnb</a> team to visit <a href="https://twitter.com/HackReactor">@HackReactor</a>. Picture of them talking about their tech stack. <a href="http://t.co/AYVDYA3JaT">pic.twitter.com/AYVDYA3JaT</a></p>&mdash; Ben Martin (@HealthfulHacker) <a href="https://twitter.com/HealthfulHacker/statuses/385258134677106689">October 2, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I don't know if [my summary of week #1](blog/2013/09/29/hackr-diary-thoughts-about-week-number-1/) made it clear or not, but although my first six days at Hack Reactor were tough, I didn't exactly struggle with any of the material. This is probably because the pre-course work was [incredibly difficult](/blog/2013/09/22/hackr-diary-pre-course-anticipation/), thereby infusing me with helpful knowledge while also shaping my expectations.

Well guess what? Week 1 was an anomaly. It was a week filled with more lectures and less hands-on programming. I knew this ahead of time, but week 2 still caught me off guard. There was quite a bit more learning with minimal guidance. Also, the joys/stresses of pair programming are turned up a few notches as a result of the additional programming time created by reducing the amount of lecture time.

Consequently, I've been feeling more tired in general. Forgive me, but spending my free time to write this blog is beginning to look less and less appealing.

I joined a nearby gym (aside: I just remembered that I need to notify Hack Reactor to get my $50 reimbursement from them!) so my energy levels should increase in a week or two. Every other lunch break is two hours long instead of just one hour long. The extra time is meant to encourage students to go exercise.

I want to write more about student life at Hack Reactor, but I think I'll just spread out the details in my [HackR Diary](/blog/categories/hackr-diary/) series rather than providing every bit of info in a single, giant blog post. So for now, I cover gym time, toy problems, and tapouts. In the future, I'll discuss the workstations, help system, student-staff interaction, food, and more.

# Week in Review

#### Toy Problems

This week, my cohort, the junior students, started solving (almost) daily toy problems, which are small coding challenges designed to get us used to the type of timed problems that will be thrown our way at tech interviews. We have to complete these problems individually. We have 30-60 minutes to think of a solution, code the solution, and submit pull requests to have an automated tester give us feedback that we can use to help fix our solutions as necessary.

#### Tapouts

This week, us juniors also started attending weekly(?) tapouts. Tapouts are like small group therapy sessions where five students voice their opinions of Hack Reactor to an alumnus. She will send anonimized feedback up the chain while also providing us with advice for any struggles we care to talk about. 

#### Special Event: AirBnB Presentation

Lead devs from [AirBnB](https://twitter.com/Airbnb) presented a ton of info about their tech stack, their work environment, [their open source project](http://nerds.airbnb.com/weve-open-sourced-rendr-run-your-backbonejs-a/), dev career advice, startup advice, etc. There was a post-presentation panel for answering several questions. Then there was a post-panel meet-and-greet session. It was a truly fantastic event.

#### Saturday Social Night

I skipped last Saturday's social night to go to a close friend's birthday celebration(s). Week 2's theme for social night was board/card games.

# What I Learned + What I Thought

#### Inheritance/Subclassing in JavaScript

The subclassing sprint was a bit frustrating at first. It took me awhile to grasp the keyword `this` because of JavaScript's tendency to pass functions around as parameters to other functions.

Upon wrapping one's brain around `this` (and the `.call()`/`.apply()` methods), there was a lot of fun to be had with the assignment that Hack Reactor gave the students. This was the first assignment involving a visual facet, and the student body reacted accordingly (with creativity galore).

#### Algorithms

The algorithms sprint was a fantastic challenge, but there was no specific set of knowledge to learn. It felt like the main goal of the sprint was to get students' minds thinking in more computer-oriented ways. We were taught some basics about time complexity, but we didn't go into much depth about Big-O notation. We briefly described actions (e.g., deleting data from an array) and algorithms (e.g., solutions to the [n-queens puzzle](http://en.wikipedia.org/wiki/Eight_queens_puzzle#Related_problems)) as constant, linear, quadratic, polynomial, and exponential (as opposed to discussing the nuances of O(c), O(n), O(n^2), O(n^c), O(c^n), etc).

The main takeaway was that we should worry more about macro optimizations (storing data in variables in a way that allows for constant-time lookup) rather than micro optimizations (improving a `for` loop so then it loops fewer times). **Micro optimizations are good, but they aren't very valuable when you're just creating prototypes, minimum viable products, etc.**

I'm somewhat disappointed that we weren't taught specific algorithms such as quicksort, binary search, etc. I'm under the assumption that all software developers need to know the "greatest hits" of algorithms. Although, I'm also under the assumption that such knowledge is more useful in tech interviews than in day-to-day coding.

#### Layout/Positioning (HTML/CSS)

I taught myself a decent amount of HTML/CSS before my cohort's start date, so I was very comfortable with the layout assignment, but it wasn't easy. There are still plenty of times when proper CSS positioning eludes me. That said, this topic doesn't provide an intellectual challenge.

The difficulty lies in getting the syntax just right and understanding hierarchy. Some students didn't learn much HTML/CSS before joining Hack Reactor, and so they had a lot to learn (box model, DOM hierarchy, CSS selectors, etc.) in a very short amount of time.

**If you're thinking of joining Hack Reactor as a student, I highly recommend you teach yourself HTML/CSS** ahead of time. HTML/CSS isn't tough to learn on your own, but it can be time-consuming even if you've got pros helping you. You may as well prepare yourself so then you can spend less time at Hack Reactor worrying about HTML/CSS and more time worrying about other technologies and concepts.

#### D3 (library)

[D3.js](http://d3js.org/) is a JavaScript library for creating data-driven visuals inside HTML documents. I thought jQuery was cool, but now I think D3 takes the cake. It's much harder to learn D3, but there is tremendous power to be had from familiarizing yourself with it.

That said, the D3 assignment left me mentally tired as hell. Like jQuery, you can easily select DOM elements, but the rest of the D3 syntax isn't so straightforward, and the general concepts for using D3 properly will feel rather foreign at first. I hope to spend more time on my own to master D3 ...when I'm not so damn tired. The key is to understand the [general update pattern](http://bl.ocks.org/mbostock/3808218).