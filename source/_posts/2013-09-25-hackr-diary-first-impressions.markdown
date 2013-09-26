---
layout: post
title: "[HackR Diary] First Impressions"
date: 2013-09-25 21:23
comments: true
categories: ['HackR Diary','Hack Reactor','coding bootcamps','TIL','JavaScript']
---

It's the end of day #3. I don't have much time to write, so this blog post is a smattering of thoughts from a fresh Hack Reactor student.

# Initial Observations

## Recap

- Day 1 and 2 are just review days covering topics and challenges covered by the pre-course work. Day 1 covered ettiquette, expectations, and recursion. Day 2 covered passing functions, a lot of JS fundamentals, and awesome advice for being successful (e.g., we talked about impostor syndrome, Hack Reactor's motivations, some job-hunting advice, etc).
- Day 3 covered paired programming, object-oriented programming (OOP), and classes (e.g., functional instantiation vs. prototypal instantiation vs. psuedoclassical instantiation).

## Logistics

- Week 1 is full of lectures. Each day is about 50% lectures, 50% coding.
- The first 6 weeks will have plenty of lectures and structured challenges. Then there is an interim week where you work on a project from home, which gives you the flexibility to travel, but the Hack Reactor staff will be offline (they basically get a 1-week vacation every 7 weeks). After the interim week is more time for your individual project, time for a group project, and time for job prep.

## Nuances

- Lunch breaks and dinner breaks are often cut short due to lectures running long.
- Lectures run long due to people asking questions.
- All teachers advocate for students to ask questions. At Hack Reactor, the students ask a TON of questions because the class atmosphere is very comfortable.
- The students are really nice. Everyone's excited to meet new people (even the quiet ones are clearly motivated to be social).
- I've heard stories of students of other bootcamps going out at night to hang out and have fun. I could be wrong, but so far it seems like there's no time/energy left for going out at night.
- That said, students don't stay here that late (so far). A lot of us leave by 9pm. I thought it'd be common to leave no earlier than 10pm, but there aren't even that many students from the senior cohort by the time the clock strikes 9:20pm (which is the latest I've stayed). I have a feeling this will change in a few weeks (beause that will be crunch time for the senior cohort).
- Nothing's perfect. Some equipment is broken, some chairs are shitty, some online resources are buggy, etc. None of these issues have been big issues.

# Nuggets of Knowledge

## Life Nuggets

### Re: **Education**

Passive learning is deceptively similar to true understanding. When you just observe a correct solution, it can give you the illusion that you learned more than you really did. For example, you might watch someone code up a good solution. When you walk away, you'll think you understand everything necessary to solve the problem, but all you learned was some code without its meaning.

### Re: **Starting a new tech career**

Everyone thinks starting a new tech career with a tiny startup is really exciting. That might be true, but people tend to forget an important caveat: less structure could lead to a less efficient roadmap to individual success.

In less formal terms, you might work for a tiny startup on something you truly care about, but the startup could easily be too small or too young to provide an environment with superiors/peers that can help you develop your programming skills (or any job-related skills).

## JavaScript Nuggets

### Guard operator

Marcus, the primary instructor, warned us that some devs dislike the guard operator, but it's really concise (which is cool to him). The guard operator is a logical-AND that "guards" a small bit of code the same way an `if` statement would guard it. For example:

~~~
if(goodStudent === true){
	candy++;
}

// The above code could be refactored into the following:
goodStudent && candy++;
~~~
{:lang="javascript"}

The following is a more practical example:

~~~
// Let's say you want to only call a function with an array if the array is NOT undefined (i.e., you want to guard against a scenario where you pass an undefined argument to a function).
arg && myFunction(arg);
~~~
{:lang="javascript"}