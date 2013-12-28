---
layout: post
title: "Queues &amp; Stacks in JavaScript (with Batman and Superman)"
date: 2013-12-26 15:54
comments: true
categories: ['JavaScript','technical posts','data structures']
---

The proverbial "they" say (says?) it's good to write technical blog posts. Blog posts that get down and dirty with the nitty gritty of low-level, in-the-weeds details and nuances accompanied by jargon, acronyms, and name-dropping are all the rage in the dev community. More importantly, I really want to help beginners learn programming, so I may as well teach some basic concepts via my blog. (Later on, I hope to contribute more to [The Odin Project](http://www.theodinproject.com/), which is a free, open-source, online resource for beginners created by a very cool individual.)

So as my first foray in technical blog posts, I present to all loveable noobs: the introductory data structures known as stacks and queues.

# What's a Stack?

A stack is a collection of items (or data) that follow a particular rule: the last item to join the collection is the first one to leave.

- The **L**ast data **I**n is the **F**irst data **O**ut (**LIFO**)
- Add data: **push**
- Remove data: **pop**
- Data enters and exits at the same end of the stack (at the **top**)

## Simple implementation

{% coderay Simple Stack (array-based example) lang:javascript http://stackoverflow.com/questions/1590247/how-do-you-implement-a-stack-and-a-queue-in-javascript Stack Overflow %}
var stack = [];
stack.push(1);  // use the push method provided by the Array prototype
stack.push(2);
stack.push(3);
console.log(stack);  // output: [1,2,3]

var popped = stack.pop();  // use the pop method provided by the Array prototype
console.log(popped);  // output: 3
console.log(stack);  // output: [1,2]
{% endcoderay %}

## Ridiculous analogy

Imagine you've found an old, abandoned well. You think to yourself, "Bruce Wayne fell down a well when he was a kid, and I wanna be just like the Batman, so I'm gonna fall down this sweet well!" But you hesitate because ...it's a well, and wells are scary, ya know?

Unbeknownst to you, [your arch-nemesis](http://batman.wikia.com/wiki/Harley_Quinn) is out walking her [pet hyenas](http://batman.wikia.com/wiki/Bud_and_Lou). She spots you, and quickly runs over to shove you into the well. She giggles in delight at the sight of your plight. She then hides and waits for more people to walk near the well so she can **push** them too.

It just so happens that this well has the diameter of a single person's width. When someone is pushed into the well, they land on top of the last person who fell in before them. This creates a **stack** of people and some rather pronounced discomfort. Eventually, there are 5 people in this deep-yet-thin well, and you decide it's time to call for help to get rescued.

To your disappointment, the not-so-dark knight named Superman arrives to pull you well-dwellers out (one at a time). The last one pushed into the well is the first to **pop** out. *LIFO.*

# What's a Queue?

A queue is a collection of items (or data) that follow the real-life "rules" of waiting in a line of people: the first item to join the collection is the first one to leave the collection.

- The **F**irst data **I**n is the **F**irst data **O**ut (**FIFO**)
- Add data: **enqueue**
- Remove data: **dequeue**
- Data exits at the: **head** of the queue
- Data enters at the: **tail** of the queue

## Simple implementation

{% coderay Simple Queue (array-based example) lang:javascript http://stackoverflow.com/questions/1590247/how-do-you-implement-a-stack-and-a-queue-in-javascript Stack Overflow %}
var queue = [];
queue.push(1);  // "enqueue"
queue.push(2);
queue.push(3);
console.log(queue);  // output: [1,2,3]

var dequeued = queue.shift();  // "dequeue"
console.log(dequeued);  // output: 1
console.log(queue);  // output: [2,3]
{% endcoderay %}

## Ridiculous analogy

Batman decides to do some in-the-field combat training. He drops into the middle of a gang meeting and yells, "I've sent your buddies to jail. I know you want revenge. Catch me if you can. P.S. I'm Batman!" Why does the cowled hero do this? We all know Batman is a smart dude, and sure enough, he has a clever plan. He lures the baddies who are running after him into a narrow alley.

The gangsters can only approach Batman one at a time to fit in the narrow alley, so they form a line (aka **queue**). The gangster at the front of the line is the first gangster knocked out (aka **dequeued**) by Batman (**first in; first out**). You might even say that Batman's fists aim for the **head** of the queue and foolish gangsters enter at the **tail** of the line of doom.

# The Story Will Continue

Stay tuned for more blog posts on data structures. My next technical blog post will examine how to implement stacks and queues from scratch (without arrays) to get a deeper understanding of push, pop, enqueue, and dequeue. I know you can't wait for the moment I deliver on this promise. I can hear your panting through my WiFi, but please stay patient. I was busy working on a [web app](https://github.com/RebootJeff/cocompare) and then a [mobile app](https://github.com/RebootJeff/phone-tag-phonegap). Now, I'm busy with job searching while possibly starting mini-project.

On a mildly amusing, unrelated note: isn't it funny to think about the phrase "stay tuned"? It's getting rather archaic now that terrestrial, over-the-air TV and radio are losing popularity. Yes, these are the random things I think about as I write blog posts.
