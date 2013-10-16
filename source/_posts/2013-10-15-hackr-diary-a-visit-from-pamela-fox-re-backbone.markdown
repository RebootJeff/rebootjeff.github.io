---
layout: post
title: "[HackR Diary] Event: Pamela Fox on Backbone"
date: 2013-10-16 20:13
comments: true
categories: ['HackR Diary','Hack Reactor','TIL','Backbone','JavaScript','event','Coursera','Khan Academy']
---

<blockquote class="twitter-tweet"><p><a href="https://twitter.com/pamelafox">@pamelafox</a> schooling <a href="https://twitter.com/HackReactor">@HackReactor</a> students on <a href="https://twitter.com/search?q=%23backbonejs&amp;src=hash">#backbonejs</a> <a href="http://t.co/1xRuxIEvKl">pic.twitter.com/1xRuxIEvKl</a></p>&mdash; andre (@AndrEvangelestA) <a href="https://twitter.com/AndrEvangelestA/statuses/389949525588062209">October 15, 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Last Monday, the Hack Reactor students were treated to [a Backbone presentation](http://backbone-3ways.appspot.com/) by [Pamela Fox](http://blog.pamelafox.org/). It was packed with a ton of insight. I frantically took notes on my smartphone (like a fool), so now I present to you a collection of cool cucumbers.

# What I Learned

## Backbone Nuggets

- Region management (which you can "outsource" to the likes of [Chaplin](http://chaplinjs.org/) or [Marionette](http://marionettejs.com/s)) is worth checking out. Apparently, they help you limit the amount of rendering you need to do by allowing you to target specific regions of the web page.

- Not all Backbone libraries are created equal! Some provide sweet functionality at the cost of depressing performance losses. The Backbone ecosystem is cool, but not entirely safe. Pamela once removed a library from Coursera's codebase that was responsible for a *full second* of page load time.

- Backbone is so flexible that you might feel like an Backbone expert one day and then feel like a noob the next day when you see someone else's radically different and compelling usage.

- Break up your views into more views. Make sibling views and nested views. No single view should be a bajillion lines of code. If you find yourself making long js files in Backbone, it's time to split things up, my fellow noob.

## General Code-Related Nuggets

- Don't optimize prematurely. Performant code is harder to read. Making code harder to read early on can be annoying.

- [RequireJS](http://requirejs.org/) kills your foolish usage of global vars. Perhaps I should use it.

- Single-page web apps can be harder to debug (than multi-page web apps?) because state gets saved across various renders. Errors can be hard to reproduce during the debugging process because there might be many user interactions that need to occur in a particular sequence to cause the error.

- **Ask potential employers about their companies' testing practices.** How much regression testing do they do? How many tests have they created? More tests means less fear when contributing to the codebase as a fresh employee.

- Making **forms** with Backbone (or any MV framework?) is great because forms lend themselves to the model-view-collection paradigm with ease. Forms are collections of questions, which are models, which have their own views. Each question view can draw from a set of views meant to provide a particular format (a view for a question answered by checkboxes, a view for question answered by text fields, a view for question answered by generic menu, etc). This also means Backbone is good for creating **control panels** for admin users (e.g., admin control panel for teacher conducting a Coursera class).

## Re: Coursera

Pamela used to work for Coursera. She drew from her experiences with that company to provide a lot of context and real-world examples for the arguments she put forth in her presentation.

- To address SEO concerns associated with single-page web apps, Coursera used Just-in-Time rendering. Coursera would detect whether or not a visitor was a search/social engine bot crawling the sit. Upon identifying the bot, Coursera servers would respond by firing up a rendered instance of the web app using Selenium. The bot would then be directed to the code produced by the rendering. This prevents the bot from crawling an HTML file that has nothing but `<script>` tags pulling in Backbone code. Side note: Google is not cool with the just-in-time technique. Coursera had to use a different technique for Google, but that was not disclosed during Pamela's talk :(

- It's not the most organized (in my opinion), but you can find a lot of Coursera code on Github here: https://github.com/coursera/forum-js-snapshot (open source, baby!)

- When viewing their source code with your browser, you'll see mostly `<script>` tags. There is very little `<body>` HTML. That's due to extensive use of Backbone.

# What I Thought

Pamela is a fantastic speaker. What I liked most about her talk was the use of real-world examples. As a student, it's always so informative to hear about life in the wild (so to speak). Seeing as how this was a Hack Reactor event exclusively for students, it's hard to judge it impartially, but I'm going to go ahead and claim it was awesome.