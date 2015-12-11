---
layout: post
title: "[Example] Refactoring to Functional JS - Combine Keyed Lists"
date: 2015-12-11 09:02
comments: true
categories:
  - JavaScript
  - functional programming
  - example code
  - technical
  - engineering
  - programming
---

## The Premise

Given a bunch of arrays kept within a JavaScript hash table (plain object), we want to extract the arrays and combine them. In other words, we're given a collection of arrays of elements and we want a single array of elements.

This example was inspired by some code I found in the codebase where I work. The use case was different, but the overall idea (extracting elements from within arrays that are within an object) is the same. To make things slightly more complex, the arrays of the input object could possibly contain `null` elements because the elements were being provided by a service that could sometimes return `null`.

### Example Input/Output


{% coderay lang:JavaScript Example Input/Output Data %}
// example input
var usersBySocialNetwork = {
  twitter: [
    { name: '@RebootJeff' },
    { name: '@doitwithalambda' },
    null
  ],
  facebook: [
    null,
    { name: 'Kevin' },
    { name: 'Bianca' },
  ]
};

// expected output
var users = [
  { name: '@RebootJeff' },
  { name: '@doitwithalambda' },
  { name: 'Kevin' },
  { name: 'Bianca' }
];
{% endcoderay %}

The output has the `null`s removed. We can pretty much assume we only want to see user objects in the output array; no other kinds of elements.

### The Original Solution

The following code snippet is a slightly modified version of someone else's work. I've changed the variable names and comments, but the core logic/algorithm is the same.


{% coderay lang:JavaScript Original Solution %}
var _ = require('lodash');

function combineKeyedArrays(keyedArrays){
  var flattened = [];

  // produce a flat Array from an Object with values that are arrays
  _.each(keyedArrays, function(array){
    flattened = flattened.concat(array);
  });

  // only return the truthy elements of flat Array
  return _.filter(flattened, function(element) {
    return Boolean(element);
  });
}
{% endcoderay %}

- The combination of `_.each` and `Array.prototype.concat` creates one big array from all the arrays within the input object called `keyedArrays`.
- The combo of `filter` and `Boolean` rids the big array of falsey values to ensure no `null` elements end up in the output.

## Let's Refactor!

### Refactor 1 - Using Lodash's Chain

{% coderay lang:JavaScript Refactored Version 1 %}
var _ = require('lodash');

function combineKeyedArrays(keyedArrays){
  return _.chain(keyedArrays)
    .reduce(concatArray, [])
    .filter(Boolean)
    .value();
}

function concatArray(arr, val) {
  return arr.concat(val);
}
{% endcoderay %}

Sadly, we need to create our own `concatArray` because Lodash doesn't have such a utility method (I swear it used to exist in an earlier version ...maybe).

Thankfully, we can actually use Lodash's `reduce` on objects (not just arrays). I see the replacement of `each` with `reduce` as a win because the end result is more expressive. `each` is vague whereas `reduce` makes it more clear that we intend to go from a collection of things (in this case, a collection of arrays) to just a single thing (in this case, just a single array).

### Refactor 2 - Using Lodash's Flow

{% coderay lang:JavaScript Refactored Version 2 %}
var _ = require('lodash');

var combineKeyedArrays = _.flow(
  _.values,
  _.flatten,
  _.compact
);
{% endcoderay %}

Now we use [function composition](https://github.com/MostlyAdequate/mostly-adequate-guide/blob/master/ch5.md) via `flow`, which uses left-to-right direction. Standard function composition via `compose` would read from right-to-left, but I prefer LTR for a more familiar aesthetic. My friends who are more advanced in [functional programming](/blog/categories/functional-programming/) assure me I'll get used to the RTL direction if I give it a shot, but for now, I protest (i.e., I'm lazy).

With `flow`, we can read `combineKeyedArrays` as a series of 3 steps. First, we extract values from an object via `values`, then we flatten the resulting array via `flatten`, then we reject any falsey elements from the array via `compact`.

Notes:

- `values` obviates the need for the combo of `reduce` + `concat`
- `flatten` is *shallow* by default
- `compact` obviates the need for the combo of `filter` + `Boolean`

> OMG WHERE DID THE INPUT/PARAMETER GO?!
>
> **--You (probably)**

We can stop referring to the input as `keyedArrays`. Our function `combineKeyedArrays` has now been written in a **pointfree (aka point-free aka tacit) style**. In other words, we no longer need to name - and refer back to - any parameter variable.

Think of it like the verbs "hit" and "type" in the English language. The word "hit" is a bit vague, so you probably should include more context or *references* for clarity. Are you hitting a person in a fight? Are you hitting some books to study? Are you hitting the bed to sleep? Are you hitting a keyboard button to type?

The word "type" is more specific. You already can infer you'll be dealing with a keyboard. You don't need to mention the keyboard at all when you use the verb "type" instead of the verb "hit".

"I'm typing UNIX commands" is more concise and direct than "I'm hitting buttons on the keyboard to issue UNIX commands". Both are valid, but the former is easier to understand even though it's less comprehensive.

### Refactor 3 - Using Ramda

Now, let's translate from Lodash to [Ramda](http://ramdajs.com/), a utility library that is much more aligned with the functional programming style. I've covered how to get started with Ramda in [an earlier blog post that one friend labeled as an "excellent summary"](/blog/2015/06/14/refactoring-towards-functional-programming-in-javascript/). I must be pretty awesome [:D](https://duckduckgo.com/?q=awesome+smiley+face&iax=1&ia=images&iai=http%3A%2F%2Fannawrites.com%2Fblog%2Fwp-content%2Fuploads%2F2012%2F03%2Fawesome-smiley.jpg).

{% coderay lang:JavaScript Refactored Version 3 %}
var R = require('ramda');

var combineKeyedArrays = R.pipe(
  R.values,
  R.unnest,
  R.filter(Boolean)
);
{% endcoderay %}

Notes:

- `pipe` is Ramda's `_.flow`. I appreciate the name "pipe" over "flow" because "pipe" reminds me of Bash's `|` operator.
- `unnest` is Ramda's *shallow* array-flattening method.
- Ramda lacks a `compact` :(
- `R.filter(Boolean)` is leveraging [currying](https://github.com/MostlyAdequate/mostly-adequate-guide/blob/master/ch4.md) / using partial application to yield the same effect as `_.compact`.

## Let's Review

We've gained so much:

- **Expressiveness!** Remember that `each` is vague. The combo of `_.chain` and `_.value` adds unnecessary boilerplate cruft compared to the simplicity of `flow` or `pipe`.
- **Brevity!** Shorter code isn't always better code, but if expressiveness and legibility remain high as code length decreases, that's generally what scientists refer to as a victory.
- **Robustness!** We're using well-tested library methods. There are fewer possible typos after refactoring to simpler code.
- **Fun!** Wasn't that so much fun?! Hell yeah it was!! [\*level-up\*](https://www.youtube.com/watch?v=qEg9wKFGtQg&t=0m05s)

By the way, possible documentation for our refactored, pointfree `combineKeyedArrays` involves a type signature as a comment, but admittedly, I'm still learning how to do proper, FP-style type signatures. Also, keep in mind that the names of your functions should help tell others what it does, and the fact that it's composed of 3 easy-to-read methods is quite helpful as well.

{% coderay lang:JavaScript Refactored Version 3 with comment for documentation %}
var R = require('ramda');

// Object<Array> --> Array (more old-fashioned)
// ...or...maybe...
// {k: [v]} --> [v] (similar to Ramda docs)
var combineKeyedArrays = R.pipe(
  R.values,
  R.unnest,
  R.filter(Boolean)
);
{% endcoderay %}

Why don't we say something more specific such as `// {k: [user]} --> [user]`? Because `combineKeyedArrays` clearly works with any type of element inside the arrays. Whoooaaaaaa...

And because I appreciate you as a cool person, here's a [Gist that has all the code in 1 spot](https://gist.github.com/RebootJeff/d8877fdbcff79ec140cf) for your future reference.
