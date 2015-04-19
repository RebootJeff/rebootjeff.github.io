---
layout: post
title: "How to Talk While Coding and Whiteboarding in 7 Steps"
date: 2015-04-19 21:13
comments: true
categories:
  - communication skills
  - Communication for Engineers
  - career development
  - dev job search
  - JavaScript
---

![Photo of whiteboarding](/images/20150419/startupstock_whiteboarding.jpg)

In [my first article on Communication For Engineers](/blog/2014/09/02/communication-for-engineers-101-we-have-a-problem/), I ranted about my disappointment surrounding engineering and communication skills. I ended that blog post with a list of communication-related topics that I promised to write about. Instead of addressing any of those topics (sorry!), this post will talk about how software engineers can improve their communication while coding collaboratively or while solving coding challenges for a job interview.

**Warning:** JavaScript is my specialty, so some of the advice below is JS-centric, and all code examples are written in JS.

#### I cooked up 7 steps for how to discuss code smoothly:

1. Draw the situation
2. Ask clarifying questions
3. Explain approach
4. Breadth-first coding
5. Refactor
6. Walkthrough
7. Testing

Notice that these steps don't magically provide a complete guide to actually solving problems. For example, they don't tell you which data structures to use. Instead, these steps show you how to communicate better as you solve a challenge. They help you talk with your interviewer or colleague about the problem space, your initial impressions, your ability to break down the problem into sub-problems, and your quality assurance process.

# The 7 Steps Explained

## 1. Drawing the Problem
Admittedly, this step could be optional. Drawing is best for folks who work well with visuals. But even if you're not an artist, you should still consider drawing a diagram or picture of the problem because visuals tend to be effective tools for communicating complex subjects and situations. For example, data structures are usually easier to talk about after you draw them out.

Furthermore, you might reveal certain questions through the act of drawing. At the very least, **drawing stuff out can help an interviewer follow you**. Going back to the data structures example: imagine you're supposed to work with a binary tree. It's easier to talk about it if you draw a tree and point to nodes rather than just saying, "First we will process the root node, then we will go to the left child and do blah blah blah. At that point, depending on the value, we might go down to the child's child or we might..."

By the way, **you don't have to stick to drawing pictures**. This step could be about writing down example data, example inputs, example outputs, example use cases; and then mapping them together by drawing arrows, circles, etc. Examples are great for communication, and they are also good for problem-solving in general. Try to think of examples that are really simple (to get a basic grasp of the problem), examples that are more realistic, and examples that are crazy (to reveal edge cases and potential validation concerns).

## 2. Asking Clarifying Questions
Do not follow any of your assumptions without asking a question first. It's tempting to hear a challenge or puzzle and immediately get into solving it. But there are real-world concerns for real-world problems, and you should demonstrate your familiarity with such issues.

Also, you can save time by asking clarifying questions during an interview because interview challenges tend to be contrived. Do you have to account for crazy input values? Does the output need to be formatted in a certain way? If the puzzle involves numbers, do you have to account for negative values, decimals, etc? Are you expected to do input validation, error handling, or memory optimization?

## 3. Explaining Your Approach

At this point, you might have a solution in mind and you're eager to get coding. Or you might just have a partial solution. Either way, take a moment to give a quick overview of the **purpose** of the code you're about to write. Also, give a sense of what **algorithms or concepts** will be implemented as part of your approach to the problem at hand.

For example, "This looks like a problem we can solve with a recursive solution that traverses all nodes of the dataset." In this example, "recursion" is the concept and traversal is the purpose.

## 4. Breadth-First Coding

When it comes time to actually write out some code (or pseudocode), write out as much as possible at a high-level before going into the low-level details. For example, if your solution requires looping over objects received from an AJAX request in order to parse some data, don't dive into that AJAX request. That's a low-level detail. Start from the high-level approach of "fetching data" and then immediately move to the next high-level step of "parsing data". With this strategy, you cover the whole breadth of the solution before diving into any detail of the solution.

In other words, write modular code by using a breadth-first mindset. Everyone knows it's a good idea to write several small functions rather than one giant function, so apply that approach to your communication too. When you explain how a computer works, you start the explanation at a high level (e.g., "hard drives store data, CPUs crunch data, ...") rather than starting at a low level (e.g., "the flow of electrons is controlled by gates known as transistors").

{% coderay lang:JavaScript Example - Breadth-First Coding %}
// Challenge (aka Prompt) - Write a function that determines the average number of
// retweets for a given user after a given cut off date.

// Phase 0 - Psuedocode (optional)
function getRetweetAverage(username, cutOffDate) {
  /**
   * 1. Fetch tweets via Twiter API
   * 2. Filter tweets based on date
   * 3. Calculate avg count of retweets from filtered data
   * 4. Return a promise that resolves to the answer
  **/
}

// Phase 1 - Coding with declarative helper functions
function getRetweetAverage(username, cutOffDate) {
  return fetchTweets(username).then(function(tweets) {
    var recentTweets = filterTweetsByDate(tweets, cutOffDate);
    return calculateAverageRetweets(recentTweets);
  });
}

// Phase 2 - Implement low-level helper functions
function fetchTweets(username) {
  // Let's pretend we're using AngularJS's HTTP request service, which uses promises.
  var params = {
    screen_name: username,
    count: 200 // FYI this is the max allowed by Twitter's API
  };
  return $http.get('https://api.twitter.com/1.1/statuses/user_timeline.json', params);
}

function filterTweetsByDate(tweets, cutOffDate) {
  return tweets.filter(function(tweet) {
    // Convert tweet's String date into a JS Date object before comparing.
    var createdAt = new Date(tweet.created_at);
    return createdAt > cutOffDate;
  });
}

function calculateAverageRetweets(tweets) {
  var totalRetweets = tweets.reduce(function(sum, tweet) {
    return sum + tweet.retweet_count;
  }, 0);
  return totalRetweets / tweets.length;
}
{% endcoderay %}

In the example above, you should write code one "phase" at a time. Starting with psuedocode is optional, but it might be a good idea to at least verbalize it if you don't plan on writing it. Then write the code in a declarative style as seen in "Phase 1". Lastly, flesh out the functionality of your solution by writing the code that actually makes things work.

By the way, I've never actually used the Twitter API, so the example code might not follow best practices or might not take into account how it actually behaves. For instance, maybe the API accepts a parameter to do the date filtering for you.

## 5. Refactoring Your First Draft

Once you've reached the point where the code seems to solve the challenge at hand, it's time to refactor. If you're writing under pressure in an interview situation, it's likely that you haven't written the cleanest code. If you're writing without any pressure, it's still good to refactor your first draft into a more readable/maintainable variant. Here's a list of tips for deciding what to refactor:

- **Improve readability** by fixing indentation, whitespace, names, etc.
  - **Rename variables** into semantic names. It's tempting to use very short variable names during interviews because you feel pressure to finish quickly. Consider renaming them into more recognizable names to show your audience that you know how to write maintainable code that potential co-workers could easily read.
  - **Replace loops** with a `map`, `filter`, `reduce`, etc where possible.
  - **Consider naming anonymous functions** if they have potential to be re-used as a helper.
- **Extract code** into helper functions. It's very common for interview candidates to inadvertently write long functions. Even if you tried to follow Breadth-First Coding in Step 4, you may have slipped.
- **Double-check promises** and look for opportunities to reduce boilerplate and anonymous functions.
  - **Check return statements** to ensure that your promises will resolve to the correct values (and that the segments of your promise chain will pass correct values).
  - **Use promise library helpers** such as `all`, `spread`, etc where possible.
- **Add error-handling**/logging for professional bonus points.
- **Rewrite in another style** (e.g., Functional Programming vs Object-Oriented Programming) for massive bonus points.

Admittedly, this Step 5 isn't as directly related to communication as other steps. It's mostly focused on improving your code. However, there is still a communiation-related opportunity here. As you are refactoring, verbalize your intentions. Discuss what you want to improve before you improve it. Explain the rationale behind the improvements. Mentions the pros and cons of your code without the improvements and with the improvements (i.e., before vs after).

## 6. Walking Through Your Answer

At this point, your code should be presentable. By following the previous steps, your audience should already have a solid, high-level understanding of your code. So now it's time to give a detailed walkthrough.

Explain any nuances, use precise terminology, and expound on any interesting control flow or references (e.g., closures in JavaScript). You can also mention any implications regarding speed, memory, I/O, security, etc. But overall, your goal is to describe your code *in detail*.

## 7. Testing Your Answer

You might actually want to perform this step before step 6, but it depends on how you roll. After you've gotten to the point where you have a solution that seems to be good, take a minute to describe how you'd make sure it's robust. When you normally write code on your own, you of course test it out by running it with various inputs or circumstances. Describe them; verbalize them.

For example, if you're writing a function with some parameters, you'll probably run the function with a bunch of different arguments with different values and maybe different datatypes.

- **Numbers:** negative values, 0, 1, odd vs even, really big numbers, decimals
- **Strings:** upper vs lower case, single character, numeric characters, punctuation and non-alphanumeric characters.
- **Object Literals:** check for weird keys (much like *Strings*)
- **Collections & Data Structures:** empty collections, only 1 item, several items, check for mutation side-effects, ascending order, descending order, random order, nested objects/arrays/other data structures.

# Where Did These Steps Come From?

I came up with these 7 steps based on...

- [advice from Gayle Laakmann McDowell](/blog/2014/05/31/dev-job-search-tips-from-the-coding-interview-guru/)
- [advice from Hack Reactor instructors](/blog/2014/05/11/hackr-diary-weeks-11-12-and-beyond/)
- my experience interviewing for jobs
- my experience conducting a handful of mock interviews for Hack Reactor grads
- my experience conducting interviews where I work (10+ so far)
