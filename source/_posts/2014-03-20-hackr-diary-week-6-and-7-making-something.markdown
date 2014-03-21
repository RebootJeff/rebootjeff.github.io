---
layout: post
title: "[HackR Diary] Week 6 and 7: App from Scratch"
date: 2014-03-21 17:12
comments: true
categories: ['HackR Diary','Hack Reactor','coding bootcamps']
---

![Personal Project presentation time](/images/20140321/co-compare_presentation.jpg)

<p class="my-caption">Presenting my project, Co-Compare, to the folks of Hack Reactor</p>

# Life Update

I got a job! I will start using my JS skills for dolla bills on Monday. I will blog all about my rather tiring job search soon. For now, I will resume blogging about Hack Reactor from [where I left off](http://rebootjeff.github.io/blog/2013/10/28/hackr-diary-week-5/). During the 2nd half of the program, I didn't do any blogging, but I took plenty of notes for the sake of blogging at a later time, so prepare to be amazed ...or mildly amused. Remember, the following rollercoaster ride took place during late-October through mid-November.

# Recap of Events

## Interim Week (different format)

The 2nd half of Hack Reactor starts with an "interim week" (aka "solo week") where expectations are a bit cloudy. **The Hack Reactor website didn't do a good job of explaining that the injection of an interim week means that Hack Reactor is really a 13-week program.** During this special week, Hack Reactor HQ is not guaranteed to be open to students. Also, students are not guaranteed any access to staff. The staff is either taking a break or working on reconfiguring the offices or other changes.

In other words, the students are on their own for starting the first week of developing their personal projects. Students self-organize if they want to meet up at a cafe or whathaveyou to enable collaboration.

## What I Did

- I spent most of my time working from HR HQ when it was open. I used nearby cafes when it wasn't.
- Like a few others, I used interim week to do some travelling and to catch up on sleep.
- At one point (maybe after interim week?), I broke my laptop by being a Linux noob. I was one of few Ubuntu users in my cohort, and I had trouble dealing with permission/access issues. I eventually followed some StackOverflow suggestion and fucked up my permissions so badly that I had to reinstall Ubuntu. As you can imagine, my emotions are still failing to heal from that self-inflicted disaster.
  - FYI, my new job is giving me a Mac. Soon I will join the majority of devs in the promise land of screens that actually reproduce accurate colors, impressive battery life, and installation wonders such as homebrew.

## Extras

- In my cohort, we organized a night to go to a movie theater for Ender's Game. Good times.
- A rep from [Famous](http://famo.us/) stopped by to give a presentation about a brand new web app framework. It's so new that even now, Famous is in beta. Back during the personal project period, it was in a closed beta (or was it alpha?), but Famous was inviting Hack Reactor students to access it! The framework renders special `<div>` elements in a breathtaking way. I never used it, but I will talk about it a bit more in another blog post.

# What I Learned

Holy. Crap. I learned so much during the personal project weeks. Admittedly, I didn't work extra long hours until the last week or so before the deadline. By then, I was working at least 80 hours per week. In the first couple of days, I realized there was so much I had to learn that it felt quite overwhelming, and I had a difficult time starting.

## Tools

Obviously I would have to learn a lot of app concepts, engineer some solid logic, etc. But I also had to do all this while learning new tools.

- **Balsamiq:** Wireframing software. Creating wireframes really helps when trying to explain what you hope to build. To practice communication skills and project management, students had to explain their progress/goals very briefly during small stand-up meetings.
- **Yeoman:** Boilerplate/scaffold generator. I used an Angular-Express generator to help me get started making a full-stack app with boilerplate code for Angular, Node, and Express. This served as a great "starter pack" of code.
- **Grunt:** Task runner. To be honest, I used Grunt simpy because it came with Yeoman. However, gaining exposure to the tool opened my eyes to the possibilities provided by task runners like Grunt.
- **Stylus:** CSS pre-processor. I'm not sure if CSS pre-processors are part of the tech stack or "just" another set of dev tools, but for what it's worth, I didn't write pure CSS for Co-Compare. Instead, I wrote Stylus CSS. I like the visual design side of front-end development, and using Stylus made that facet even more fun.
- **Heroku:** Web app hosting provider. It's easy to use because it follows a git workflow, but deployment still has challenges (re: environment configuration).

## The Tortured (ok not really) Birth of An Idea

I like to think my mind is superior --errr...I mean *creative*. However, it can be tough to come up with web app ideas based on constraints. Everyone worried about whether or not they could actually implement their ideas in just a few weeks (I think it amounted to only 2.5 weeks). In the end, I learned that "Just Do It" really applies. You can spend roughly 3 gajillion hours analyzing ideas, use cases, market needs, tech stacks, visual design, etc. But at some point, you need to just do it already. Just make something and see what happens. The price of failure is time spent. The gain of failure is lessons learned. A beauty of programming is the ability to quickly change, pivot, redo, etc.

### From Cool to Meh

Originally, I thought my idea was too boring. I wanted to create a fantasy sports game specifically for tennis, but I couldn't find a good way to get the data/stats from pro tennis matches, so I switched to something far less cool.

I switched to an idea spawned by my love for analyzing/comparing products and services. In the past, I've spent far too much time comparing video game consoles, cars, computer parts, *bootcamps*, etc. I enjoyed it too. A lot. But I knew most people aren't crazy in this way, so I worried that my app idea for [Co-Compare](http://cocompare.herokuapp.com) (a web app to build comparison tables and have others vote on them) was too unsexy.

### From Meh to Oooh

It's true that Co-Compare doesn't have a ton of wow-factor, but it provided plenty of opportunity:

- **Simplicity:** It was the type of idea that could work with very few features (good for rapid prototyping).
- **Exploration:** But I could have fun adding more and more features as I desired. There were plenty of sub-ideas to explore and keep my brain satiated with more goodies to engineer.
- **Fundamentals:** My app requires CRUD actions. Create, Read, Update, and Delete are fundamental app actions that devs should know. It's weird to "brag" that Co-Compare helped me learn *fundamentals*, but it's important, and it's not easy just because it's "fundamental." Engineering a CRUDy app is a great learning experience.
- **Full-Stack:** My app covered a lot of territory so it exposed me to CSS pre-processors, front-end MVC, API design, databases, user authentication, etc. This was really scary at first, but afterwards, I was truly proud of what I covered.

I really believe that the full-stack nature of Co-Compare solidified my abilities as a web app developer. By creating a nice-looking front-end, my own API, and back-end models for a SQL datastore, I learned so much that it gave my confidence a tremendous boost --which is funny because I had a ton of confidence going into the personal project weeks...then I lost a lot of confidence when nothing I created worked the first time. So at the end, I regained a lot of confidence that I already had at the beginning.

Note: Some of my classmates implemented ideas that had very bare front ends because all the impressive stuff was run on the server side. Other folks created apps that had little or no back-end logic. The number of things wrong with these paths is quite small. In fact, most experts would say the number rhymes with "hero." Anyway, my point is that this particular "full-stack" facet of my experience is not the "best" way, but just something that I really value for myself.

## Dev Cycle/Process

Hack Reactor staff helped students with their projects by giving recommendations on tech stack decisions, dev tools, deployment options, etc. And of course, they gave us debugging help, but there was no hand holding.

The primary form of guidance came in the form of some project management structure. We formed small groups that held its members accountable for short-term goals. The staff taught us about iterative development and the concept of creating MVPs (minimal viable products) as milestones rather than aiming for creating versions that were 100% complete.

In other words, I learned about some dev processes to help promote productivity as a software engineer.

# Want to Learn from My App?

You can find the code for Co-Compare on my GitHub. I took the time to write up a decent README too because for some reason, I have a good time writing English in addition to JavaScript. I suggest you [check this out](https://github.com/RebootJeff/co-compare#development) if you're interested in learning more about how I created an app from scratch.

Keep in mind that you shouldn't follow everything I do. For example, my Angular app folder structure neglects best practice. It was a popular structure at the time, but it's actually best to name folders based on features, rather than just lumping all controllers together, all views together, etc.
