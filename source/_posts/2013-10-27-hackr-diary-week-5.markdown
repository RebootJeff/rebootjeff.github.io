---
layout: post
title: "[HackR Diary] Week 5: Final Sprints"
date: 2013-10-28 22:42
comments: true
categories: ['HackR Diary','Hack Reactor','coding bootcamps','Ruby','Sinatra','ActiveRecord','AngularJS']
---

![caltrain](/images/20131028/caltrain.jpg)

<p class='my-caption'>Good morning</p>

No more sprints! I'm both sad and relieved. The sprints have provided enough structure to ensure a guided education thus far. They've equipped me with enough skill to yield the self-belief that I can actually build a complete web app ...which is good because that's exactly what I'm going to do starting this week. Looking back on week 5 makes me think I might miss the relative safety of paired programming, but I'm pumped to be diving into my own project.

By the way, this blog post is really long. I think I'm going to split up future blog posts, and I'm going to post more frequently.

# Recap of Events

### Alumni Panel

Early in the week, there was a truly invaluable guest speaker event. Six Hack Reactor alumni held a Q&A session with current students. One alumnus is a Hacker-in-Residence at Hack Reactor. His role is a paid, part-time, short-term job supporting the school. There are a handful of Hacker-in-Residences at HackR at any given time. After their stints, they are put through the same job finding process that students who didn't want to become a Resident normally go through.

The other five alumni were from Adap.tv, Adobe, DocuSign, Edmodo, and Versal, respectively. They had a variety of roles including smartphone app development, front-end MVC engineering, internal QA, data visualization, and full-stack development. I have to admit that I was a bit judgemental about the QA role at first, but it actually sounded legit by the end of the Q&A session. For what it's worth, the Adap.tv guy was hired even though he doesn't have a college degree! In my opinion, that's awesome, and it really says a lot about the meritocracy found in the tech job market (...or the non-traditional, new-school nature of the Bay Area).

There was a ton of insight gleaned from the alumni panel. Examples of advice include:

- Ask employers about their onboarding process (smaller companies might not have one, and that can be a turn-off for some newbies).
- Invest in social capital. Wow, that was a really buzzwordy sentence so let me translate: get to know your co-workers. "Ask them out" to coffee breaks, happy hours, lunches, etc. This may sound like basic networking at first, but I think the point is that in software development, you're going to be asking others for help quite a lot, so it's good to build a rapport ASAP to make asking for assistance as natural as possible. This is something I never really considered before, but after all the paired programming I've done at Hack Reactor, it makes a ton of sense to establish rapports that foster collaborative vibes.
- Ask employers to set up a meeting between you and your potential boss. It's ok --this is totally ok. I used to work in an industry where this would never really be possible, so I had to ask if this is ok after one alumnus mentioned how one of his prioties when job hunting was to find a cool boss. I want a cool boss too!
- NEVER make the first move for salary negotiations. Let them make an offer before you start specifying any numbers.
- Specific to HackR: Don't be too eager to accept your first job offer. You will get more. Shop around. It's tempting to accept your first or second job offer just because employment is such a major goal when deciding to join Hack Reactor in the first place. However, joining Hack Reactor isn't something you do just to get a job --it's something you do to get an *ideal* job.

Sorry, but I forgot to take thorough notes during the alumni panel, so the list above is rather short.

### More Guest Speakers

Now might be a good time to point out that Hack Reactor has guest speakers at least one evening per week. Attendance is optional. Oftentimes students choose to work on their assignments/projects at the workstations rather than stay in the lecture area to listen to the guest speaker.

What's my point? This week was the first time I didn't really have enough time to fully invest in the guest speakers. Rudely, I've forgotten that names of the speakers, but one guy spoke about databases (i.e., engineering decisions you might face when designing/creating/maintaining/scaling a database) and another guy (from Khan Academy) spoke about [React](http://facebook.github.io/react/), the JavaScript library written and open-sourced by Facebook. Relevant link: [React presented at JSConf](http://www.youtube.com/watch?v=GW0rj4sNH2w)

### Picking Personal Projects

To be honest, I wasn't thrilled with the way HackR arranged the transition from sprints to personal projects. Students were under the impression that we'd get more support/attention for coming up with project ideas, but we weren't given much time to brainstorm. Instead of dedicating a lecture to a guided brainstorming session, students had to come up with ideas in their spare time (which is tough when busy worrying about Ruby and Angular for the sprints).

### Social Night: Haunted House

Once again, I did not attend social night. On one hand, I feel bad that my cohort has generally had low participation in the weekly social nights. On the other hand, the consensus seems to be that the social nights just don't feel all that appealing. The first one was awesome; the others were "meh."

Instead of going to the Social Night event last Saturday, I went to a nice happy hour/dinner with a few other students. Afterwards, I went back to HackR to continue tackling client-side user authentication with my Angular sprint partner. We failed, but we got a lot of other stuff done during the day, so I felt ok about the sprint as a whole. Plus, my partner and I established a fun rapport so even failing to get "auth" working was a funny time.

# What I Learned

Week 5 included assignments for building a URL shortening web app to further improve students' full-stack skills.

### Ruby, Sinatra, ActiveRecord, SQLite

Server-side code used a lot of Ruby and Sinatra. HackR chose not to teach us students Ruby on Rails (RoR) because Sinatra is simpler than Rails. It's easy to be bummed about this, but in hindsight, I'm not worried about it. Yes, Rails is a big deal right now in Silicon Valley, but I'm under the impression that RoR was embraced because of it's great for rapid prototyping. Times are changing though. There are now more options for rapid prototyping. More importantly, I'm at the point in my HackR-guided education where I have built up enough fundamental know-how to make me confident that I can learn RoR later.

For now, it's more important to learn concepts about MVC/MV* development, user authentication, databases, etc. Speaking of databases, there isn't much for me to say about SQLite because students were harnessing ActiveRecord magic to manipulate a simple SQLite database with only two tables. We had to use [tux](https://github.com/cldwalker/tux) to do database probing, which is slightly less convenient than using MySQL's terminal interface (as we did in the previous week).

### Angular

The students were pretty hyped up to learn Angular as our final sprint. We've invested a lot of time into learning Backbone, but word on the street (a really nerdy street) is that Angular is the "new hotness" that will take over the world of front-end JavaScript for single-page web apps.

Overall, I think the students' reception of Angular was torn. Some love the power (Angular's data-binding is pretty addicting); some find discomfort in the need to learn some rather bizarre syntax (Angular forces you to write HTML with "directives").

Here's the low down: Backbone feels like the traditional, familiar option whereas Angular feels like the more experimental, exotic option. Yes, it took us awhile to appreciate Backbone, but once we got comfortable with it, we realized how easy it is to comprehend after you get your mind around it.

For Angular, the learning curve is a lot less steep, but it also seems like it will be harder to master. There is more "magic" ...and now I'm realizing I should explain that word.

#### Aside: What is "magic"?

When I say "magic," I'm using it colloquially to refer to abstraction that feels harder to comprehend and feels less intuitive. For analogy\*, a door knob abstracts mechanical bits. You may not be a locksmith, but it's probably easy for a child to imagine how it works. Even as a child, you probably had some intuition that door knobs just have some simple mechanism for converting rotational movement of the knob into longitudinal movement of the latch On the other hand, it's a bit hard for a child to imagine how a digital camera works. Even an old-school film-based camera feels magical at that tender age when you're first capable of comprehending door knobs. Ahhh...those were the days, am I right?

**\*By the way, can we make "for analogy" a thing in the same way that "for example" is a thing?**

Also, if you google "parts of a door knob," you will see some complex diagrams, but I will defend my analogy! For the sake of argument, let's just say door knobs use simple cams.

#### Back to my thoughts on Angular

So why does Angular seem so magical? By using Angular's library of directives, you can have the browser display a list of items without writing DOM-manipulating code (i.e., jQuery). You can sort those items without writing a sorting function. You can filter those items without writing a sorting function. In Angular, you're not supposed to use jQuery to change/update the HTML on the page. Angular takes care of that for you. How does it do that? Magic (directives). I haven't even touched Angular's feature that allows you to just create your own semantic HTML tags (e.g., `<tab><pane>Content for Pane 1</pane><pane>Content for Pane 2</pane></tab>`).

### Routers, Templates, User Authentication

With MVC frameworks comes routers and templates. With web apps comes user authentication (sometimes).

On the server-side, routing involves RESTful APIs, which are fairly tidy interfaces that allow clients to talk to servers. On the client-side, routing involves flow control and updating the URL in the browser address bar so that it looks pretty/semantic. For example, you may want to switch to an editing panel when the user clicks a button. The router changes the URL to end in `/edit` without causing the page to refresh. The router also calls a function that might do edit-related things such as rendering an editing panel.

Templates are used to create sections of HTML that will contain dynamic content. Let's say you want to render an unordered list (`<ul></ul>`), and the app will determine how many items (`<li></li>`) will be in the list. Templates take care of that.

On the server-side, routing and templating is pretty easy with Sinatra. On the client-side, routing with Angular feels easier than routing with Backbone. Templates are way easier in Angular for me.

In any case, I find user authentication isn't very straightforward, but I haven't tried many gems for Ruby nor [Passport](http://passportjs.org/) for Node.js. You need to check for authentication, redirect visitors as necessary, encrypt passwords (AND usernames --don't forget that), save login info into a database, manage sessions/cookies, etc. A surprising amount of mistakes can be made.