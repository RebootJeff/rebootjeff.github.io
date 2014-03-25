---
layout: post
title: "[HackR Diary] Weeks 8-10: No More Solo"
date: 2014-03-23 15:52
comments: true
categories: ['HackR Diary','Hack Reactor','coding bootcamps']
---

![something something Mighty Ducks](/images/20140324/SimoneAnne-8351-birds.jpg)

<p class="my-caption">Insert inspirational metaphor relating birds to teamwork</p>

# Junior-to-Senior Transition

As I mentioned [last time](http://rebootjeff.github.io/blog/2014/03/21/hackr-diary-weeks-6-and-7-making-something/), my [HackR Diary](http://rebootjeff.github.io/blog/categories/hackr-diary/) was on hiatus for a bit, so the events described in this blog post occurred back in mid-November thru early-December of 2013. Weeks 8, 9, and 10 of my Hack Reactor experience covered a group project period where students formed small teams to create web apps from scratch.

I forgot to mention a few points in my description of the personal project period:

## Client Projects

Some folks in my cohort accepted client projects rather than coming up with their own web app ideas. This meant they had to meet with clients, deal with external requirements, etc. Some had fun experiences; some had frustrating experiences. Some got paid; some volunteered. They all got to add some extra gravitas to their resumes/CVs.

## Being a Senior

The cohort before mine graduated from the program just before interim week. After interim week, my cohort returned to HR HQ to find a new "junior" cohort, and there was a transition to seniorhood for us. As a senior, you have fewer/shorter lectures, less guidance, and you're given more freedom to explore on your own. You still have a schedule to follow, but it's far less rigid, which is fantastic. It's funny how you feel more freedom, yet you end up working harder because of the nature of project periods at Hack Reactor.

Unfortunately, there isn't much time to get to know the juniors when you're a senior. We had one code review night where seniors gave juniors feedback on their classwork, but as a senior, your mind is always worried about your project, your app, your baby born of code.

By the way, I noticed that the juniors had more diversity. They had more women and more minority folks. I'm not saying my own cohort felt shitty because of the percentage of white males, and I'm not saying the new junior group reached some sort of ideal diversity (eventually, I may write a rambling blog entry about my views on diversity). I'm just noting the "slope" created by two "points of data." The junior cohort was larger by about 5 or so people, but the increase in diversity was still noticeable. That said, I also noticed Hack Reactor felt more crowded (doh!).

# Recap of Events

I teamed up with 3 of my fellow seniors to work on a smartphone game called Phone Tag. Gameplay is like a free-for-all laser tag. Players sneak up on one another and hit a button to tag. The game displays a map (via Google Maps) to show locations of other players, power-ups, respawn points, etc. The app consists of HTML, CSS, and full-stack JavaScript. The client app is "ported" into an iOS app and an Android app via a tool called PhoneGap. Phone Tag leverages geolocation and real-time communications.

The first week just consisted of setting up boilerplate code and brainstorming game ideas. It took us awhile to settle on the free-for-all game mode. We originally considered implementing a game resembling zombie tag instead. My team also had to spend lots of time researching libraries, tools, smartphone abilities, and all that sort of goodness to find out what we should use to develop our project.

## Fitness Challenge: Push-Up Routine

I'm sure some Hack Reactor folks (Hackers React? Hacker Reactions?) cynically roll their eyes at the staff's efforts to promote health, but I appreciate them. For one week, there was a push-up challenge where students were encouraged to pair up and hold each other accountable for completing a set of push-ups twice a day. I paired up with a junior, and it was cool to be able to get to know someone outside of my cohort.

## Hacker-in-Residence Program

In the middle of the group project period, the staff told seniors about a program to extend the Hack Reactor experience. The Hacker-in-Residence program is an extra 3 months where you get paid to work part-time for the institution (develop internal tools, teach beginner-level content, interview applicants, etc) and work on more projects (i.e., extra project periods). The idea is that a select few seniors can become Hacker-in-Residence and gain valuable experience. I chose not to apply for the program because I already felt well prepared to enter the job market. Many students felt the same way, but plenty of them were attracted to the HIR program. Under half of the seniors applied, and most of them were accepted.

Therefore, about 1/3 of my cohort became HIRs. It's important to note that Hack Reactor might not include these guys in their post-graduation employment stats. But even so, I know previous HIRs have had little to no trouble getting employed after their HIR phase ended.

## New Hack Reactor Admissions

At some point during weeks 8-10, Hack Reactor launched their new website. It's quite a bit nicer than their last version, but more interestingly, they changed their admissions process too. The new process uses their website to check very basic JS skills.

Hack Reactor likes having students/alumni contribute to their official blog, and I anwered the call for volunteers by authoring [this blog post](http://www.hackreactor.com/blog/the-hack-reactor-interview-process-questions-and-tips) about the admissions process. Sadly, much of my experience lost relevance when the staff produced a new admissions process. I had to go through a 2-stage interview process, but now there is only a single interview. However, I think a lot of the advice I provided still makes sense.

# What I Learned

Much like the personal project period, a lot was learned via trial-by-fire work during the group project period. My group tried and scrapped various features, libraries, tools, project management strategies, etc. It was so tough and so awesome at the same time.

## Tech

My team knew we wanted to use geolocation, but we weren't certain about much else. This meant that we had to research and explore many options. Eventually, we settled on a tech stack featuring quite a few different libraries/tools.

### PhoneGap

I spent a lot of time wrestling with PhoneGap, a dev tool for creating smartphone apps using tech normally reserved for web browsers. It's a fairly popular option for informational smartphone apps, rapid prototyping, etc. However, 101 out of 62 doctors have concluded that PhoneGap can lead to headaches and irritable demeanor. I've written specifically about using PhoneGap for Android in [a past blog post]().

### Other Tech Fail

- jQuery-UI
- RequireJS vs PhoneGap (file protocol)

## Engineering

- debating
- architecture: client-side vs server-side

## Project Mangement

- MVP / what to prioritize
  - dropped: testing, user auth, NoSQL database
- staying on task / meeting MVP milestone deadlines
- division of labor
