---
layout: post
title: "Pair Programming Impressions and Tips"
date: 2015-06-12 01:33
comments: true
categories:
  - Communication for Engineers
  - programming
  - technical
  - communication Skills
---

![two rubber ducks pair programming](/images/20150612/pair_programming_ducks.jpg)

<p class="my-caption">This is the best photo I've ever taken.</p>

Some programming friends think I'm crazy, but I most definitely <3 pair programming. I dig the human interaction. I appreciate enduring the horrors of debugging with a comrade. I love the anti-ego culture.

On top of all that, pairing reduces the risk of burnout for a couple of reasons. Firstly, the average level of focus stays high throughout the day so you don't have to work as many hours. Secondly, any stress, tedium, and brain workouts are shared by two folks instead of one. Therefore, individuals are less likely to get overwhelmed or feel alone in handling responsibilities or overcoming blockers.

Admittedly, there are times when I want to get in the flow by myself without the need to constantly talk to another person, but usually, I embrace 1-on-1 talks. Why? (1) Discussion activates more of my brain. (2) [I'm a big fan of communication skills](http://rebootjeff.github.io/blog/categories/communication-for-engineers/). (3) Considering another individual's perspective gives me more to think about, and I love thinking about thinking.

For nearly 2 years, I've been pair programming. During this time, I've picked up on a few tips and pet-peeves. Read on for some musings on software development in dynamic duos.

## Communication Tips
These tips are good for all communication, not just pair programming. But bad communication skills become an unavoidable problem when you pair up, so consider improving how you talk and listen to become a better paired engineer.

#### Tone: be inquisitive, not accusatory
Another way to put it: be curious about your own assumptions, conclusions, and judgements. Unless you are 100% certain, give your partner the benefit of the doubt.

> - **DO:** What if X? Will that affect idea Y?
> - **DON'T:** Your idea (Y) won't work because of X.

> - **DO:** What are the obstacles? Let's see if we can tackle them together.
> - **DON'T:** I imagine what we need to do should be easy. Why don't you think so?

#### Precision: be specific; use idiomatic terms; avoid vague pronouns
The below example is more pertinent to a senior teaching a junior, but even proficient engineers get out of sync when generic words like "that one" are used instead of precise words like "the *[insert object name]* at *[insert context or line number]*."

> - **DO:** The promise returned by the request at line 31 will resolve with a response body containing the JSON we need to parse and possibly flatten.
> - **DON'T:** That method call will give us the data we need to check out.

## Keyboard & Mouse Tips
Maybe it's just me, but I find it painful to watch someone use only arrow keys to move a cursor or use slow mouse movements to scroll to the top or bottom of a file. Although, I admit that I could be a tad unfair in the typing department ([I rock triple-digit WPM](http://10fastfingers.com/speedtests/generate_screenshot_result/1_102_508_0_0_96_0_97.96_3086_151253) so ...booya).

- Please learn general typing shortcuts such as moving the cursor to beginning/end of word/line/file. Use these cursor movement shortcuts in conjunction with shift/delete to select/remove code quickly.
- Learn IDE shortcuts such as multi-selection/cursors, vertical/block selection, switching tabs, and deleting current line.
- Use the mouse to point at parts of the screen, not your finger. You don't want to block parts of the screen with your hand/arm, and you don't want to reach over to your partner's monitor if you've got a setup with dual-mirrored-monitors.
