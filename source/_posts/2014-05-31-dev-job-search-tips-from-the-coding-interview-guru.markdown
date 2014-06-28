---
layout: post
title: "[HackR Diary] [Dev Job Search] Tips from the Coding Interview Guru"
date: 2014-05-31 20:37
comments: true
categories: ['dev job search', 'Hack Reactor', 'HackR Diary', 'career development']
---

<blockquote class="twitter-tweet" lang="en"><p>Author of Cracking the Coding Interview, <a href="https://twitter.com/gayle">@gayle</a> , talking to <a href="https://twitter.com/HackReactor">@hackreactor</a> <a href="http://t.co/aVbcohgqSG">pic.twitter.com/aVbcohgqSG</a></p>&mdash; Jeff Lee (@RebootJeff) <a href="https://twitter.com/RebootJeff/statuses/423949825587945472">January 16, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

In a [previous post](/blog/2014/05/11/hackr-diary-weeks-11-12-and-beyond/#overtime-support), I mentioned that attended a talk given by [Gayle Laakmann McDowell](http://www.technologywoman.com) when she visited Hack Reactor. She's the author of the famous *Cracking the Coding Interview*, which is a book that helps developers perform better when interviewed for a new job. Her text mostly focuses on algorithm challenges, but there's also a lot of content that has more to do with coaching up interview candidates.

I really liked McDowell's presentation at Hack Reactor. There were plenty of intriguing anecdotes, and of course, there was plenty of good advice. Plus, she included a lot of insight into the hiring process. Many of her stories and comments provided the Hack Reactor community with a "behind the scenes" sort of perspective.

Keep in mind that she worked for companies like Apple, Microsoft, and Google, so **her advice comes from the perspective of giant companies**. I doubt her tips apply equally to smaller employers. For example, McDowell heavily emphasized the importance to study certain algorithms (e.g., various sorting and searching algos) and data structures (e.g., trees, hashes, etc). In my experience mostly interviewing with smaller companies (fewer than 500 employees; as few as 5 employees), studying textbook algorithms and data structures wouldn't have helped me as much as studying more web-specific skills.

That said, I still want to share some of the more interesting takeaways from McDowell's talk.

# Interviewers' Process / Employers' Perspective

- Your performance is evaluated relative to other candidates (so you're not just being judged based on fixed benchmarks).
- Resumes are barely read. You must make yours easy to skim within 15 seconds.
- Unless it's a warm-up question, you are not expected to get the solution right away.
- Employers judge your GitHub and public repos based on coding style ([do you violate any major no-nos?](https://github.com/airbnb/javascript)) and use of [design patterns](http://addyosmani.com/resources/essentialjsdesignpatterns/book/). They don't have much time to judge app architecture.
  - *My 2 Cents:* Perhaps this falls under "design patterns", but I would like to add that there is time to judge your use of a framework. If the employer is familiar with the frameworks you used, they will notice when you fail to follow the framework's more important conventions. For example, for AngularJS apps, I will notice if you put too much logic in the views, if you abuse $rootScope (which is akin to relying on global scope variables as a crutch), if you create bloated controllers, if you lack services/factories/providers, etc. I will be extra happy if I see you use multiple modules, if I see tests, if I see usage of Angular best practices, etc.
- Only the interviewer knows how well you did in the interview. You may think you aced it. You may think you bombed it. [But you don't really know](http://www.technologywoman.com/2011/03/31/why-your-interview-performance-is-impossible-to-judge/).

{% blockquote --Gayle L. McDowell %}
When I was at Google, I referred a number of candidates, and ran a little (informal) experiment. How well could people judge their performance?
After each candidate completed their interview, I’d ask them how they did. Then, I’d look up their actual performance. And guess what? There was no correlation. None. Zip. Zero. Zilch.
{% endblockquote %}

# Interview Coaching / Advice

- When answering a behavioral/experience question, you should tell a story. Your story-telling should use the following format: Premise, Situation, Action, Result. The "premise" is a quick, 1-sentence intro like "One time, I had to do X for an app." The "situation" is the context of your story. The "action" and "result" are pretty self-explanatory. I imagine Laackmann's motivation for this advice is that interviewees usually leave out at least one of these four parts when discussing valuable past experience.
- For each major experience you include on your resume, you should be prepared to discuss what you liked, what you disliked, what was challenging, and how you solved difficult problems/bugs.
- Always follow up with interviewers afterwards. Send them thank-you emails and ask about next steps.

## What to Worry About

- Your conversational skills don't need to be great because employers are desperate for technical skills.
  - *My 2 Cents:* I think this is dangerous advice. It might apply to a giant company, but if you're joining a smaller team, you need to be decent at chatting. Culture fit is also a bigger concern for smaller companies, and most company cultures include "must be decently articulate" as a core component.
- Worry less about super advanced algorithms, but you should worry a lot about the common algorithms and data structures such as: hashes, trees (and common tree methods such as depth/breadth-first search), binary search, merge sort, and quick sort.
  - *My 2 Cents:* I disagree. If you're aiming for a back-end job, then maybe you need to be more of an algo+data structures expert. But if you're aiming for a front-end or full-stack job, then there are more practical concerns that you will be quizzed on. I'm happy I know tree search methods, but this kind of knowledge only helped me in a few of many interviews I did during my job search. This topic of "advanced algorithms vs practical concerns" is commonly debated, but I have my reasons, which I hope to discuss in a future blog post. For the record, I've conducted interviews at my current job. I ask practical questions that most candidates struggle with.
- You must know Big-O, recursion, and maybe even bit-wise.
  - *My 2 Cents:* I disagree about the bit-wise stuff (although, I suppose it's impressive if you can bust it out with ease).

## Whiteboarding Tips

- If you are asked a trivia question, and you don't know the answer, consider reasoning the answer by imagining how things should work. For example, if asked a question about CSS, imagine you created CSS. How would you implement a given rule?
  - *My 2 Cents:* This one's iffy because a lot of trivia questions are meant to focus on unintuitive situations. A quick aside for a quick example: [margin collapsing](https://developer.mozilla.org/en-US/docs/Web/CSS/margin_collapsing). If there are two sibling `<div>` elements, and they both have `margin: 10px;`, then how much space is between them? You'd expect there to be 20px of space between them, but instead, there is only 10px thanks to margin collapsing.
- When solving an algorithm question, come up with some test cases (including edge cases!).
- Think out loud when trying to solve an algorithm question. Don't just write code.
  - *My 2 Cents:* As someone who has interviewed dev candidates, I can't stress this enough.
- When whiteboarding, be conscious of your handwriting, alignment, etc.
- It's ok to...
  - start solving a problem via pseudocode before writing real code. Just let your interviewer(s) know your plan.
  - write `TODO` comments in your code for important-but-tangential stuff like input validation
  - create proper variable names at first and then switch to abbreviated versions
- Use "breadth-first coding": write your code to use helper functions that may not exist. Write the helper functions later as needed. Think of it like writing an outline before writing an essay so then other people can quickly get a grasp of your overall approach rather than waiting and awkwardly watching for several minutes while you write out everything.
  - *My 2 Cents:* This sounds like a no-brainer, but you'd be surprised how many people don't do this. To be fair, this is like writing modular code BEFORE refactoring.
- Beware of common bugs you might make regardless of how awesome you are. Examples:
  - off-by-one errors
  - bad comparison operators in if-statements, loops, and other conditionals
  - math where you must perform a check before performing the operation to prevent edge cases from making your program explode. E.g., it might be good to perform a check before performing division so then you stop divide-by-zero errors.
