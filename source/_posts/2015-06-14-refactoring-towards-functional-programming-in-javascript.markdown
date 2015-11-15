---
layout: post
title: "Refactoring Towards Functional Programming in JavaScript"
date: 2015-06-14 13:58
comments: true
categories:
  - engineering
  - programming
  - technical
  - JavaScript
---

![Ramda.js logo](https://camo.githubusercontent.com/0b4c12a5daec02b72e6e6879861ac70f75046e65/687474703a2f2f72616d64612e6a637068696c6c697070732e636f6d2f6c6f676f2f72616d646146696c6c65645f323030783233352e706e67)

This is not a "What is FP?" guide that uses JavaScript. If that's what you're looking for, you'll love [Brian Lonsdorf's free GitHub-based guide](https://github.com/DrBoolean/mostly-adequate-guide). For this blog post, I will assume you already know currying and composition. I won't assume you know functors, monads, and the other funky whatchamacallits that I'm still trying to learn for myself.

There are a lot of blogs and presentations that answer "What is Functional Programming?" and "Why bother with Functional Programming?". There aren't a lot of resources answering "How do I start using Functional Programming in REAL life?". Most intro-to-FP resources leave you feeling like you're supposed to just drop everything and start coding from scratch in Haskell or an FP-focused language that transpiles into JavaScript (e.g., [Elm](http://elm-lang.org/) and [ClosureScript](https://github.com/clojure/clojurescript)).

My team at work has recently been exploring FP in JavaScript by using a library called [Ramda](http://ramdajs.com/). It's a functional programming JavaScript library. Ramda offers some common FP utilities to help you code in the FP style or just slowly convert parts of your codebase to the FP style.

Most of the team is unfamiliar with FP, so rather than diving into massive re-writes to convert large chunks of code from Object-Oriented Programming to FP, we've been starting small. Along the way, we've learned some solid steps for introducing FP into an existing codebase at a comfy pace. The gist of it is: don't dive into the world of endofunctors, monoids, and catamorphisms. Instead, focus on treating functions differently by cutting down on anonymous functions, subdividing functions into tiny functions, and using the simplest FP concepts such as currying and composition.

## Code smells

These are some signs that code is very imperative and not very FP-like:

- **Anonymous callbacks** - It's harder to re-use functions that don't have names, it's harder to write pointfree code with anonymous *callbacks* in particular, and function expressions will be more commonplace when you start using more FP (due to frequent use of `curry` and `composition`).
- **Suboptimal parameter order** - Function signatures should have parameters arranged in an order that fits currying. This means putting config-like parameters first and main data parameters last (which is pretty much the exact opposite order that we're all used to).
- **Loops** - In JS, loops are usually for-loops that iterate over collections. There are specialized methods such as `map`, `reduce`, and `filter` that can perform the most common looping operations in a style that is more functional and declarative.
- **Localized mutation** - This is a bit harder to explain, but local mutation (usually limited to the scope of a single function and a few nested anonymous callbacks) generally seems innocent enough until you realize it makes it more difficult to split up your functions into tiny functions, which is a major part of refactoring towards FP.
- **Side-effects from functions** - One of the major principles in FP is that [functions should be pure](https://github.com/DrBoolean/mostly-adequate-guide/blob/master/ch3.md). When functions affect data outside their own local scope, it is usually due to IO actions or an OOP construct such as a method operating on the properties of its context object.

## Refactoring steps

### Easy Difficulty

- **Use named functions** - This will make it easier to write pointfree code and to compose functions.
- **Use predicates** - Functions that encapsulate conditional statements can be composed with other functions for the FP/declarative equivalent of imperative control flow.
- **Refactor loops via `each`, `map`, `filter`, `reduce`, etc** - Using these FP iteration functions encourage you to also write small helper functions and predicates. They will guide you towards more FP.

### Medium Difficulty

- **Focus on simple FP utilities** - `R.curry`, `R.compose`, `R.composeP`, `R.prop`, `R.is`, `R.has`, `R.anyPass`/`R.allPass` are all worth checking out. Set a goal to use these as much as possible. It's a great (and reasonable!) goal to get started with the FP style without getting too overwhelmed.
  - Using `curry` and `compose` get you to the heart of FP's flexibility. Your code will look significantly different once you start currying and composing functions.
  - Dot notation for accessing properties that will be used as input to a function (use `R.prop` or `R.has` as needed).
- **Simplify all functions** - Break down larger functions into smaller functions; break down helper functions into more and more generalized helper functions.
  - Minimize the number of arguments
  - Write pure functions as often as possible
- **Segregate mutation/state** - If mutation/state is absolutely necessary, then try to separate the mutation into a traditional function and the rest into something that can be more FP-like. For example, if a function called `foo` changes some parent scope variables in addition to performing some calculation, then change `foo` so it calls two helper functions: the parent scope manipulation is done by one helper function while the calculation is done by another helper function.

## Getting Comfortable

What can you expect as you start writing FP code?

- Function names should be very expressive and more verbose.
  - ...which leads to code that looks more semantic.
- Higher-level functions should be composed of smaller, lower-level functions.
  - Making functions from functions will look/feel like a tree of nested functions.
  - Lower-level functions should be only a handful of lines (and 1-line functions become common-place). Higher-level functions might also be really short because they just rely on calling multiple functions without much additional logic.
- Remember: Function compositions are normally read from right to left.
- Debugging may be tricky at first, but you should be able to easily test lower-level functions, which means higher-level functions should be less fragile.
  - For debugging with `console.log`, you may have to add it to compositions. E.g., `var processData = R.compose(calculateStuff, logFilteredData, filterData);` You can find a more detailed example of this logging tactic later in this blog post.
- Naming functions becomes even more important; names no longer always start with verbs because they are often treated as data (nouns) rather than actions/procedures (verbs).
  - However, due to FP's relative obscurity, naming conventions are not as widespread, which could lead to codebases with poorly named functions (significantly more helper functions means more opportunities to get function names messed up). Make sure your team is on the same page for nomenclature.

## Examples

Keep in mind that I'm using [Ramda.js](http://ramdajs.com/) for these examples.

### Ex: Filtering an array

{% coderay lang:JavaScript Example - Filtering for odd numbers and multiples of 6 %}
var originalArray = [1, 2, 3, 4];

// Bad - using a for-loop to mutate a new array
var filteredArray = [];
for(var i = 0; i < originalArray.length; i++) {
  var number = originalArray[i];
  if(number % 2 || number % 6 === 0) {
    filteredArray.push(number);
  }
}

// Better - using the native Array filter method with a typical anonymous function
var filteredArray = originalArray.filter(function(number) {
  return number % 2 || number % 6 === 0;
});

// Most Functional - using predicates with a filter method
var isOdd = function(number) {
  return number % 2;
};
var isDivisibleBySix = function(number) {
  return number % 6 === 0;
};
var isValid = R.allPass([isOdd, isDivisibleBySix]);
var filteredArray = R.filter(isValid, originalArray);
{% endcoderay %}

The "most functional" technique may seem unappealling because it requires so many lines of code, but it's vital to remember that predicates serve as re-usable, easily testable utilities. Also, `R.allPass([isOdd, isDivisibleBySix])` is more expressive than `number % 2 || number % 6 === 0`. In the latter case, readers must remember how `%` works and how the result is a number that gets coerced into a boolean value for truthiness/falsiness.

### Ex: Debugging via console.log

{% coderay lang:JavaScript Example - Adding a logger for debugging %}
// Let's try to debug the following function
var processData = R.compose(calculateStuff, sortByDate, filterByStatus);

// First, we need an FP-friendly logger that works with composition
function log(note, input) {
  console.log(note + ' --- ' + input);
  return input; // this return is vital
}

// Second, we insert the logger into the composition to check if filtering worked
var processData = R.compose(calculateStuff, sortByDate, log('filtered data'), filterByStatus);

// Then we run processData with some data, check the log output, and adjust
// the placement of the log within the composition until we find where
// things go wrong.
{% endcoderay %}

Once again, it may seem a tad painful. You're being forced to create a special logger function. But much like in the previous example, keep in mind that you're being forced to create specialized functions that will probably be useful enough to be part of your project's internal library of utilities and helpers.

### Ex: Promises
Let's pretend we need to grab data about an animal.
First, we query our database of animals.
Second, we use our query results to get more info from a 3rd-party animal API.
Third, we use some part of that info to search for relevant photos from the Flickr API.

{% coderay lang:JavaScript Example - Writing promise chains %}
// Bad - using typical anonymous function boilerplate
function getAnimalData() {
  return getAnimalInfoFromDatabase().then(function(response1) {
    return getRelevantInfoFrom3rdPartyAPI(response1);
  }).then(function(response2) {
    return getRelevantPhotoFromFlickrAPI(response2);
  }).then(function(response3) {
    return response3;
    // Note: This last part of the promise chain is actually unnecessary, but
    // newbies tend to include it.
  });
}

// Better - using pointfree style
function getAnimalData() {
  return getAnimalInfoFromDatabase()
    .then(getRelevantInfoFrom3rdPartyAPI)
    .then(getRelevantPhotoFromFlickrAPI);
}

// Most Radtastic - using Ramda's promise composer
var getAnimalData = R.composeP(
  getRelevantPhotoFromFlickrAPI,
  getRelevantInfoFrom3rdPartyAPI,
  getAnimalInfoFromDatabase
);
// Notice how the order of composition goes from right to left.
{% endcoderay %}
