---
layout: post
title: "[HackR Diary] My Formal Apology"
date: 2013-11-19 21:53
comments: true
categories: ['HackR Diary','Hack Reactor','coding bootcamps','software development']
---

My previous blog post was nearly 3 weeks ago. Why? What's stopped me from posting more stories of life at Hack Reactor? For the past several days, I have been working on an individual project. I was very confident going into it, and I should eventually blog specifically about the initial stages, but as it turned out ...there is a crap-ton of stuff to juggle when developing a web app. There are so many things that can go wrong in your workflow --not just in your code.

# Things That Kept me Busy

- Defaut installation of node/npm on Ubuntu led to file permissions issues. Oh shit.
- Figuring out Yeoman: Before `npm install -g yo`: I wonder what will happen. After `yo generator-angularexpress`: What is all this stuff?! Oh nice.
- Figuring out Grunt: How can I get it to work with Stylus? Oh nice.
- Easy, but time-consuming (to make sure you don't break something that used to work)
  - Organizing files/folders in a professional way (inter-file `require` statements can break)
  - Using environment variables (typos can be devastating)
- Facebook Authorization
  - Making 2 FB apps (one for dev environment; one for production environment)
  - Figuring out the proper callback URL
- Databases
  - Juggling MySQL in development environment, then switching to PostgreSQL in production.
  - Why is the production database getting flooded? Oh there's a random configuration setting I missed in Sequelize.
- Random Heroku hiccups (at one point, a node module provider went down, causing Heroku's `npm install` to die).

These are just a few of the little obstacles that add up. You don't see them coming. They take quite a bit of time to hunt down.

# Nerdy Chuck Norris Jokes

As an apology for not blogging much in the past 3 weeks, here are some jokes from **[the best API ever](http://www.icndb.com/)**:

All arrays Chuck Norris declares are of infinite size, because Chuck Norris knows no bounds.

Chuck Norris doesn't have disk latency because the hard drive knows to hurry the hell up.

Chuck Norris can't test for equality because he has no equal.

Chuck Norris burst the dot com bubble.

All browsers support the hex definitions #chuck and #norris for the colors black and blue.

MySpace actually isn't your space, it's Chuck's (he just lets you use it).

Chuck Norris can solve the Towers of Hanoi in one move.

Chuck Norris finished World of Warcraft.

Chuck Norris doesn't use web standards as the web will conform to him.

Whiteboards are white because Chuck Norris scared them that way.

Chuck Norris can delete the Recycling Bin.

Chuck Norris's beard can type 140 wpm.

Chuck Norris can unit test entire applications with a single assert.

Chuck Norris doesn't need sudo, he just types "Chuck Norris" before his commands.

Chuck Norris doesn't need a debugger, he just stares down the code until the bug confesses.

The class object inherits from Chuck Norris

Chuck Norris knows the last digit of PI.

Chuck Norris' Internet connection is faster upstream than downstream because even data has more incentive to run from him than to him.

Chuck Norris's keyboard has the Any key.

Chuck Norris can install iTunes without installing Quicktime.

Chuck Norris's OSI network model has only one layer - Physical.

Chuck Norris compresses his files by doing a flying round house kick to the hard drive.

Chuck Norris uses canvas in IE.

Chuck Norris's database has only one table, 'Kick', which he DROPs frequently.

Chuck Norris's brain waves are suspected to be harmful to cell phones.

Chuck Norris sits at the stand-up.

Chuck Norris has never registered an account. He just logs in.
 
Code runs faster when Chuck Norris glares at it.
