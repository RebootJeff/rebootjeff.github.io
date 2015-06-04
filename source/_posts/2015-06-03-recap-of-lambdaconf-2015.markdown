---
layout: post
title: "Recap of LambdaConf 2015 - Where Brains Explode"
date: 2015-06-03 20:39
comments: true
categories:
  - conferences
  - technical
  - functional programming
---

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">Can you intuit that these slides are about promise-land of virtual filesystems inspired by <a href="https://twitter.com/hashtag/FunctionalProgramming?src=hash">#FunctionalProgramming</a> ? <a href="http://t.co/AGiupUies9">pic.twitter.com/AGiupUies9</a></p>&mdash; Jeff Lee (@RebootJeff) <a href="https://twitter.com/RebootJeff/status/602129973067952128">May 23, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

On May 21st, I traveled to Boulder for [LambdaConf 2015](http://www.degoesconsulting.com/lambdaconf-2015/), a functional programming (FP) conference. Overall, it wasn't as beginner-friendly as I had hoped, but it gave me plenty of food for thought as I explore FP. Today, I'm going to summarize some key points and takeaways from the talks that really stuck with me. I didn't understand everything I heard, but still learned a thing or two ...I think.

# Recaps

## Keynote: "Ipecac for the Ouroboros" by Paul Phillips
Apparently, the [Ouroboros](http://en.wikipedia.org/wiki/Ouroboros) (serpent eating its own tail) in this talk represents all programmers (and perhaps even all computer users) who are eating their own tails by accepting the current model for filesystems (files, folders, directories, etc). Phillips suggests that he has the cure (the ipecac).

What if computers used virtual filesystems? Imagine if filesystems were more like databases, and retrieving files would be like using expressions that define queries and which files to retrieve. You would not need to rely on knowing filepaths and file names. You wouldn't end up with multiple copies of the same files/folders in various directories. You would rely on useful metadata to get your latest photos. You could even ask for "all the photos with person X" (via facial recognition).

## "Selfish Purity: How Functional Programming Makes Every-Day Jobs Easier" by Daniel Spiewak
Spiewak claims that FP gurus suck at articulating to non-FP programmers about why FP rocks. According to him, FP's strengths boil down to reasonability, testability, and concurrency.

As a beginner in the world of FP, I partially agree. For me, it's easy to grasp why FP rocks in theory, but sometimes it's hard to understand in practice because it can be so difficult to start writing FP code.

Instead of going on about abstract algebra, Spiewak says FP evangelists should emphasize **reasonability, testability, and concurrency**. For intro classes, FP teachers should focus less on manipulating data and more on how to do data-centric programming instead of behavior-centric programming.

### Reasonability
FP emphasizes data over behavior, and it's easier to reason about data than behavior (especially if the behavior can be different due to side-effects, implicit inputs, etc --in other words, impurity makes it difficult to reason about behavior).

### Testability
Side-effects leads to difficult testability leads to devs hating testing leads to devs writing fewer/poorer tests leads to lower software quality. This plagues the software industry.

Using FP algebra leads to simpler logic and better testability. By writing a "real" interpreter that performs side-effects and a "fake" interpreter that inspects, testing becomes easy. Free monads enable this pattern. Free monads make it easy to write these 2 "interpreters".

### Concurrency

- sequential ~ `flatMap` or `for-`comprehensions ~ monads
- Parallel ~ `zip` ~ applicatives

*Note:* In case it isn't obvious already, I had trouble comprehending this part of the Spiewak's talk. My understanding is that the purity of FP lends itself to easily distributing computation of expressions and composing the results.

## "Why I Like FP" by Adelbert Chang
Imperative programming requires you to maintain state in your head. At the very least, you have to remember values stored in all sorts of variables, maybe different state for each iteration of a loop, etc. With imperative programming, your brain uses a lot of energy on maintaining state (and types in an untyped language) when it should be focused on just solving the problem. This is really annoying if you love the expressions from physics/math where you simply derive solutions to problems.

Math has referential transparency (algebra is just lots of substitution), which is straightforward. FP brings referential transparency (and therefore, more algrebraic concepts) into programming.

## "How I Learned Haskell in 5 Years" by Chris Allen
Or: Thoughts on **teaching** Haskell (and just "teaching" in general).

Allen is a professional Haskeller, but he also does a lot of teaching. He spent a lot of time introducing co-workers to the language, and he eventually created a [free guide on Haskell](https://github.com/bitemyapp/learnhaskell). It was great to hear his perspective on education in the realm of coding.

- It took Allen 5 years to learn Haskell because he went through unproductive cycles: complete a tutorial, try a practical project, get frustrated, stop ...repeat.
- When he first started teaching, he sucked at it. He emphasizes that his first audiences were test subjects, and novice teachers should be grateful to their first audiences.
- His Haskell book, *[Haskell Programming from first principles](http://haskellbook.com/)* is for self-learners and doesn't assume recent Computer Science education. It doesn't even assume programming experience because going from something like JavaScript to Haskell will feel like starting from scratch anyway (yikes!).
- Handwaving over explanations is problematic. Allen warns that teachers should avoid giving definitions before explanations. That tactic runs counter to how **humans learn via intuition and informal observations that eventually coalesce into formal explanations**.
- I found a few particularly interesting blog posts by Allen:
  - [The problem of learning functional programming](http://bitemyapp.com/posts/2014-12-31-functional-education.html)
  - [Meditations on learning Haskell](http://bitemyapp.com/posts/2014-04-29-meditations-on-learning-haskell.html)

## "Programming and Math" by Harold Carr
Boom: [http://www4.di.uminho.pt/~jno/ps/pdbc_part.pdf](http://www4.di.uminho.pt/~jno/ps/pdbc_part.pdf)

# Further Impressions

## FP in the real world
Functional programming used to be considered rather academic and unpractical, but nowadays, there are a lot of languages and corresponding communities that make FP friendlier and useful. Consequently, there are plenty of people using FP for "real" software.

## FP languages
Judging from the conference, Scala, Clojure, and Haskell are the most popular functional programming languages. Haskell seems to have the fewest programmers, but the most momentum/interest. Not only is Haskell favored by the purists, but its static type system is lauded as being the near-panacea that programmers don't realize they need until they learn it.

However, I saw enough Clojure code to walk away impressed by it. It seems far less intimidating than Haskell, but perhaps that's largely due to my background in JavaScript (JS and Clojure are both dynamically typed). The funny thing is that there seemed to be a theme where Clojure developers end up finding enlightenment in Haskell thanks to its strict ways. Perhaps learning Clojure is the perfect stepping stone for learning Haskell? If you're intrigued, check out:

- [Clojure for the Brave and True](http://www.braveclojure.com/getting-started/#1__First_things_first__What_is_Clojure_), an online book
- [ClojureBridge](https://github.com/ClojureBridge/curriculum/tree/gh-pages), organization providing workshops and a free online curriculum
- [Nightmod](https://sekao.net/nightmod/), a Clojure-based game-making tool
