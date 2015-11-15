---
layout: post
title: "Why fast code matters even when phones have octa-core CPUs"
date: 2015-11-16 10:29
comments: true
categories:
  - engineering
  - programming
  - technical
  - web development
  - performance
  - JavaScript
---

Have you seen the new Nexus 6P smartphone? It packs a "system on a chip" that features *two* CPUs, each with *four* cores. Surely it can run your JavaScript code without breaking a sweat, right?

![Snapdragon 810 promo material](/images/20151116/ss_snapdragon810.png)

## Writing Performant Code is Hard

It’s true that really low-level performance optimizations often don’t feel like they’re worth learning or worrying about. You’ve got to deal with complicated business logic and juggling user data and state! You don’t have time to record CPU profiles for every new function you write!

On top of that, **computers keep getting more powerful, right?**

## But What Does the Future Hold?

Here’s the insight*: if you’re targeting laptops/desktops, then you can probably feel safe about imperfect code in many respects. However, **the trend of computers getting more powerful isn’t what it seems.**

### Devices speed up after slow starts

Look at the trend from a bigger picture perspective: modern tech has gone from powerful desktops to less powerful laptops (and netbooks and Chromebooks!) to even less powerful smartphones/tablets to much less powerful wearables and IoT devices. Consider that smartphone apps might not be so popular if web apps were more performant earlier in the history of iOS, Android, and web views.

*\*Disclaimer:* I can’t take credit for the insight. I read it somewhere on the Internet, and I don’t remember where. Probably Quora though.

I’ll also add my own thought to chew on: Memory optimizations might still be important as folks browsing the web tend to leave a ton of tabs open and don’t close/reopen their browsers as often as they used to.

## What's a well-intentioned developer to do?

To be fair, browsers have come a long way. And it can be tough to care about tiny performance optimizations when browsers might end up handling them for you. For example, string concatenation used to be a no-no in JavaScript. The recommended best practice was to use `Array.prototype.join` instead of string concatenation.

This "best practice" is now [very outdated](http://archive.oreilly.com/pub/a/server-administration/excerpts/even-faster-websites/writing-efficient-javascript.html).

Like most decisions in reality, there will be trade-offs and ROI concerns. Like most decisions, the right answer is probably somewhere in between two extremes. Like most of my commentary on this blog, I'm dispensing info with JavaScript in mind, but some takeaways are language-agnostic.

My decision-making process for how to spend my time on performance involves a few key points:

- Always stay curious about current best practices.
- Don't learn a "best practice" and expect it to remain "best" forever. If someone teaches you a performance optimization tactic, check the Internet to make sure it's still relevant.
- Focus on higher-level performance optimizations (e.g., learning [performant animation techniques](https://blog.codeschool.io/2015/09/11/how-to-keep-web-animations-from-slowing-you-down/), shaming nested loops/traversals, plugging memory leaks, refactoring to recursion for [Tail Call Optimization](http://www.2ality.com/2015/06/tail-call-optimization.html)) rather than lower-level concerns (e.g., `while` loop vs `for` loop, `i++` vs `++i`, etc).
- Learn how code is actually digested by your target platform (e.g., for browser-based apps, [learn the Critical Rendering Path](https://www.udacity.com/course/website-performance-optimization--ud884), learn the [JavaScript Event Loop](http://blog.carbonfive.com/2013/10/27/the-javascript-event-loop-explained/) --and Web Workers as a bonus).
- Readability matters. If other devs can't understand your code because of obscure micro-optimizations, then you're probably hurting the team. Consider sacrificing the optimizations to prioritize collaboration.
- Keep dreaming for the day when platforms will optimize your code for you! Just kidding. It's kinda sorta already happening ([learn about JIT compilers](https://twitter.com/RebootJeff/status/603281637070123008)).

I've noticed many of my "key points" really just boil down to "do your best, buddy!" Freaking brilliant.

#### P.S.
Because JavaScript is single-threaded, the multi-core loveliness of modern CPUs doesn't directly help your web app unless you use web workers. There will be some benefit regardless of web workers just because the phone has to worry about more than just your web app (background apps, managing sensors, etc).
