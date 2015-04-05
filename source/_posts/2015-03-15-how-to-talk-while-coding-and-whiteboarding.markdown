---
layout: post
title: "How to Talk While Coding and Whiteboarding in 7 Steps"
date: 2015-03-15 21:13
comments: true
categories:
  - communication skills
  - Communication for Engineers
  - career development
  - dev job search
---

In [my first article on Communication For Engineers](/blog/2014/09/02/communication-for-engineers-101-we-have-a-problem/), I ranted about my disappointment surrounding engineering and communication skills. I ended that blog post with a list of communication-related topics that I promised to write about. Instead of addressing any of those topics (sorry!), this post will talk about how software engineers can improve their communication while coding collaboratively or while solving coding challenges for a job interview.

#### There are up to 7 steps for smoother communication while coding:

1. Draw the situation
2. Ask clarifying questions
3. Explain approach
4. Breadth-first coding
5. Refactor
6. Walkthrough
7. Testing

Notice that these steps don't magically provide a complete guide to actually solving problems. For example, they don't tell you which data structures to use. Instead, these steps show you how to communicate better as you solve the challenge. They help you talk with your interviewer or colleague about the problem space, your initial impressions, your ability to break down the problem into sub-problems, and your personal quality assurance process.

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

// Phase 1 - Psuedocode
function processTweets(username, cutOffDate) {
  /**
   * 1. Fetch tweets via Twiter API
   * 2. Filter tweets based on date
   * 3. Calculate avg count of retweets from filtered data
   * 4. Return a promise that resolves to the answer
  **/
}

// Phase 2 - Coding with declarative helper functions
function processTweets(username, cutOffDate) {
  return fetchTweets(username).then(function(tweets) {
    var recentTweets = filterTweetsByDate(tweets, cutOffDate);
    return calculateAverageRetweets(recentTweets);
  });
}

// Phase 3 - Implement low-level helper functions
function fetchTweets(username) {
  // Let's pretend we're using AngularJS's HTTP request service, which uses promises.
  return $http({
    method: 'GET',
    url: 'https://api.twitter.com/1.1/statuses/user_timeline.json',
    params: {
      screen_name: username,
      count: 200 // FYI this is the max allowed by Twitter's API
    }
  });
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

## 5. Refactoring Your First Draft

- Promises (e.g., `Q.all`)
- Readability
  - Rename variables
  - Replace looping over collections with map, filter, reduce, etc when possible
- Extract code into helper functions
- Add error-handling/logging for professional bonus points
- Rewrite in another style (e.g., Functional Programming vs Object-Oriented Programming) for bonus points

## 6. Walking Through Your Answer

- Demonstrate detailed understanding of your own code
  - Demonstrate you know how the computer will run your code
- Call out any particularly good parts, weak parts, potential bottle-necks, etc.

## 7. Testing Your Answer

You might actually want to perform this step before step 6, but it depends on how you roll. After you've gotten to the point where you have a solution that seems to be good, take a minute to describe how you'd make sure. When you normally write code on your own, you of course test out your code by running it with various inputs or circumstances. Describe them; verbalize them.

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
- my experience conducting 10+ (so far) interviews where I work
