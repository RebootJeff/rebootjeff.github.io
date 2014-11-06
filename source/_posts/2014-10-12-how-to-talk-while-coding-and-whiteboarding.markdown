---
layout: post
title: "How to Talk While Coding and Whiteboarding in 7 Steps"
date: 2014-10-12 21:13
comments: true
categories:
  - communication skills
  - Communication for Engineers
  - career development
  - dev job search
---

In [my first article on Communication For Engineers](/blog/2014/09/02/communication-for-engineers-101-we-have-a-problem/), I ranted about my disappointment surrounding engineering and communication skills. I ended that blog post with a list of communication-related topics that I promised to write about. Instead of addressing any of those topics (sorry!), this blog post will talk about how software engineers can improve their communication while coding collaboratively or while solving coding challenges for a job interview.

#### There are up to 7 steps for smoother communication while coding:

1. Draw the situation
2. Ask clarifying questions
3. Explain approach
4. Breadth-first coding
5. Refactor
6. Walkthrough
7. Testing

Notice that these steps don't magically provide a complete guide to actually solving problems. For example, they don't tell you which data structures to use. That still requires solid computer science skills. Instead, these steps show you how to communicate better as you solve the challenge. They help you talk with your interviewer about the problem space, your initial impressions, your ability to break down the problem into sub-problems, and your personal quality assurance process.

# The 7 Steps Explained

## 1. Drawing the Problem
Admittedly, this step could be optional. Drawing is best for folks who work well with visuals. But even if you're not an artist, you should still consider drawing a diagram or picture of the problem because visuals tend to be effective tools for communicating complex subjects and situations. For example, data structures are usually easier to talk about after you draw them out.

Furthermore, you might reveal certain questions through the act of drawing. At the very least, **drawing stuff out can help an interviewer follow you**. Going back to the data structures example: imagine you're supposed to work with a binary tree. It's easier to talk about it if you draw a tree and point to nodes rather than just saying, "First we will process the root node, then we will go to the left child and do blah blah blah. At that point, depending on the value, we might go down to the child's child or we might..."

By the way, **you don't have to stick to drawing pictures**. This step could be about writing down example data, example inputs, example outputs, example use cases, etc. Examples are great for communication, and they are also good for problem-solving in general. Try to think of examples that are really simple (to get a basic grasp of the problem), examples that are more realistic, and examples that are crazy (to reveal edge cases and potential validation concerns).

## 2. Asking Clarifying Questions
Do not follow any of your assumptions without asking a question first. It's tempting to hear a challenge or puzzle and immediately get into solving it. But there are real-world concerns for real-world problems, and you should demonstrate your familiarity with such issues.

Also, you can save time by asking clarifying questions during an interview because interview challenges tend to be contrived. Do you have to account for crazy input values? Does the output need to be formatted in a certain way? If the puzzle involves numbers, do you have to account for negative values, decimals, etc? Are you expected to do input validation, error handling, or memory optimization?

## 3. Explaining Your Approach

## 4. Breadth-First Coding

## 5. Refactoring Your First Draft

## 6. Walking Through Your Answer

## 7. Testing Your Answer
- **Numbers:** negative values, zero, one, odd versus even, really big numbers
- **Strings:** upper/lower case, single character, numeric characters, non-alphanumeric characters
- **Object literals:** check for weird keys (much like *Strings*)
- **Collections and data structures:** empty collections, only 1 item, several items, check for mutation side-effects, ascending order, descending order, random order, nested objects/arrays/collections/data structures.

# Where Did These Steps Come From?

I came up with these 7 steps after...

- hearing [advice from Gayle Laakmann McDowell](/blog/2014/05/31/dev-job-search-tips-from-the-coding-interview-guru/)
- hearing [advice from Hack Reactor instructors](/blog/2014/05/11/hackr-diary-weeks-11-12-and-beyond/)
- my experience searching for a job earlier this year
- my experience volunteering to conduct mock interviews for Hack Reactor grads
- my experience conducting interviews where I work

# More Tips

### Use Collaborative Language
Say "we" instead of "I" as much as possible to cultivate a sense of collaboration and teamwork. You probably noticed that teachers tend to use inclusive words like "we". It just feels better. If you do paired programming, it becomes more natural. E.g., "First **we** will iterate over the array and process the elements to make a new array. **Let's** do this with Array.map()"

### Handwriting Matters
If your handwriting sucks, slow down and put some effort into writing neatly. It's really annoying to have to decipher ugly handwriting. It's much worse when it's ugly, handwritten *code*. It might not be a deal-breaker, but it can make a smooth road into a bumpy one.

### What Do YOU Care About?
Ask yourself, "If I were hiring engineers right now. What would I care about when interviewing them?" You probably use some intuition and real-world concerns to answer that question. Your answers can help you perform better during an interview. Some examples:

- You probably care that a candidate can identify potential issues. Can they come up with example edge cases?.
- You probaby want to see if a candidate knows best practices. Is their code clean, testable, modular, performant?
- You likely care about collaboration. Can this candidate communicate well? Do they write code that's easy for others to read?

Take these questions and make sure you "answer" when you are interviewed. As you write code during an interview, mention that you are doing XYZ to improve readability, mention that line 4 is a best practice, mention that you set up the function to be more testable by doing ABC. And so on.

### Discover A New Perspective
To dive deeper into the previous tip, try conducting a mock interview of a friend. Imagine what it's like to be the interviewer rather than the interviewee. Now imagine that you're a busy engineer who has to use valuable time to interview someone. Use that perspective to identify ways to make life easier for the interviewer. Some of my advice might sound stupid until you think of interviews from the interviewer's perspective (e.g., ugly handwriting).

### Skip around
When solving a problem, you usually want to break it down into smaller sub-problems. After you do that, you might find that some sub-problems are harder to conquer than others. That's fine. Via breadth-first coding, it should be easy to skip a sub-problem and come back to it later. This way, you maximize the amount of time in which you can demonstrate confident coding.

For example, let's say you have 15 minutes to complete a challenge. You've divided the problem into 3 parts. The 2nd part is really tough. The 1st and 3rd parts are easy to conquer in 5 minutes each. Well go ahead and solve the easy parts in the first 10 minutes and leave the rest for the 2nd part. That would be better than finishing the 1st part, getting stuck on the 2nd part, and not even starting the 3rd part. This advice is pretty much the classic "skip and come back" advice pertaining to quizzes, exams, tests, etc.
