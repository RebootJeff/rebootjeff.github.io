---
layout: post
title: "Queues & Stacks from Scratch with JS Patterns"
date: 2014-01-04 16:04
comments: true
categories: ['JavaScript','technical posts','data structures','design patterns']
---

In my [previous post](/blog/2013/12/26/queues-and-stacks-in-javascript/), I began my quest to help noob programmers by introducing the basic computer science topic of data structures. I provided a quick overview of queues and stacks, so please read all about 'em before engaging your eyeballs with this blog post. This time around, we'll check out four different patterns for creating classes in JavaScript while learning how to build stacks and queues from scratch.

Before we go, I should warn you that I'm going to focus on describing the class instantiation patterns rather than thoroughly explaining the implementation of the data structures. Just keep in mind that we are going to explore building stacks and queues with objects rather than arrays. More specifically, we will use a property called `storage` that is an object, not an array. Now I know what you're pondering.

> Why?

That is a beautiful question. Please ask it all the time (but please don't troll me by leaving "Why?" in the comments section of this blog post). In this case, the answer to "Why?" may be a tad disatisfying. The answer is "because we can", but don't worry! It'll be fun. Now, let's start instantiating some motherhugging classes.

# 1. Functional Instantiation

The simplest way to implement classes is with a "maker" function that creates a new instance of the class and returns that instance so it can be stored as a variable. The new instance is just like any other JavaScript object. It can have properties that store relevant information about the instance (e.g., with a `Car` class, instances might have a `price` property). It can also have properties that store functions. These functions serve as **methods** that are tightly associated with the instance.

#### Characteristics

- Creates new copies of the same functions when creating a new instance of the same class. This lack of reuse takes up more memory and can leave an unsavory taste in some programmers' mouths.
- There is no quick way to modify all instances of the class after they've been created. This will become more clear after examining the other instantiation tactics.
- Private variables can be created/used by harnessing **closure scope** superpowers, but I won't get into that today.
- If you understand JavaScript functions and objects, then you can understand classes implemented via functional instantiation (other instantiation techniques require knowledge of `this` and/or `new`).
- Could be used to create callable instances (i.e., the class could return a function rather than an object filled with properties).

#### Example code:
{% coderay Stack from scratch (functional instantiation) lang:javascript %}
var makeStack = function(comment){
  // Provide private variables in closure scope
  var size = 0;
  var storage = {};
  var instance = {};  // Start building an instance of Stack class

  // Add extra properties for the hell of it
  instance.annotation = comment;

  // Add functions to the instance to serve as methods
  // (they will provide an interface to the stack's storage)
  instance.push = function(data){
    storage[size] = data;
    size++;
  };

  instance.pop = function(){
    if(size > 0){  // Only perform pop actions if the stack has data
      size--;
      var data = storage[size];
      delete storage[size];  // Don't forget to delete from storage!
      return data;
    }
  };

  instance.size = function(){
    return size;
  };

  return instance;
};

// Create and use an instance of the Stack class
var myStack = makeStack("I'm a stack! Whoa.");
myStack.push(1);              // myStack stores 1
myStack.push('b');            // myStack stores 1 and 'b'
myStack.push(3);              // myStack stores 1, 'b', and 3
console.log(myStack.pop());   // logs 3
console.log(myStack.size());  // logs 2
{% endcoderay %}

# 2. Functional Instantiation w/Shared Methods

By utilizing an object filled with methods, several classes can be created that have the same methods without creating new copies of said methods. The classes will use their own function references to refer to the same set of shared methods. Therefore, using shared methods eats up less memory than functional instantiation *without* shared methods.

#### Characteristics

- Reuses functions (which conserves memory) by getting function references from a utility such as [Underscore.js](http://underscorejs.org/#extend)'s `_.extend(instance,methods)`.
- Retains the same benefits as functional instantiation *without* shared methods.

#### Example code:
{% coderay Queue from scratch (functional instantiation with shared methods) lang:javascript %}
var makeQueue = function(queueName, comment){

  // You can use object literal notation for `instance` (instead of dot notation),
  // but then we have to use `this` and we lose the privacy of closure scope
  // (e.g., `storage` is no longer private), so this kind of sucks.
  var instance = {
    name: queueName,
    annotation: comment,
    head: 0,
    tail: 0,
    storage: {}
  };

  // The _.extend() function is provided by the Underscore.js library
  _.extend(instance, sharedQueueMethods);

  return instance;
};

// The object below stores methods that could be shared with other classes
var sharedQueueMethods = {
  enqueue: function(data){
    this.storage[this.tail] = data;
    this.tail++;
    // The tail points to the next EMPTY "spot" for data to be stored
    // it does NOT point to the last OCCUPIED "spot" in the storage
  },
  dequeue: function(){
    if(this.head <= this.tail){  // Check the queue's size
      var data = this.storage[this.head];

      // Deleting is even more important for queues than for stacks
      // (memory leaks are a bigger threat for queues)
      delete this.storage[this.head];
      this.head++;
      return data;
    }
  },
  size: function(){
    return this.tail - this.head;
  }
};

// Create and use an instance of the Queue class:
var myCoolQueue = makeQueue("Jeff's Queue",'Hello, world!');
myCoolQueue.enqueue('a');             // myCoolQueue stores 'a'
myCoolQueue.enqueue(2);               // myCoolQueue stores 'a' and 2
myCoolQueue.enqueue('c');             // myCoolQueue stores 'a', 2, and 'c'
console.log(myCoolQueue.dequeue());   // output: 'a'
console.log(myCoolQueue.size());      // output: 2
{% endcoderay %}

# 3. Prototypal Instantiation

The key to prototypal instantiation is the use of `Object.create()` to utilize shared methods. Unlike functional instantiation with shared methods, there is no need to use an `extend()` function.

While it's possible to use a prototype's functions with `Object.create(ExampleClass.prototype);`, it's also possible to (ironically) avoid the word "prototype" altogether by using `Object.create(sharedMethods);`.

#### Characteristics

- Reuses shared functions via `Object.create(Example.prototype)` or `Object.create(objectOfFunctions)`.
- Unlike functional instantiation, function references are shared. Each instance of the class does not get its own function references that point to the shared methods. This saves even more memory (although it is a very small improvement).
- Unlike functional instantiation, there is no way to use closure scope to enforce privacy of variables.
- Variables are stored on the returned object (aka `instance`), which means the shared stack methods need to use the keyword `this` to access the necessary data. It's not a huge bummer, but if you're a beginner, then `this` can be a confusing concept.
- Can use prototype chains for dynamic method modification and inheritance (subclasses!).

#### Example code:
{% coderay Stack from scratch (prototypal instantiation) lang:javascript %}
var makeStack = function(comment){
  var instance = Object.create(sharedStackMethods);
  instance.annotation = comment;
  instance.size = 0;
  instance.storage = {};

  return instance;
};

var sharedStackMethods = {
  push: function(data){
    this.storage[this.size] = data;
    this.size++;
  },
  pop: function(){
    if(this.size > 0){
      this.size--;
      var data = this.storage[this.size];
      delete this.storage[this.size];
      return data;
    }
  },
  size: function(){
    return this.size;
  }
};

// Create an instance of the Stack class:
var myStack = makeStack("I'm a stack! Whoa.");
// Using the instance doesn't change from one class pattern to another
myStack.push(1);              // myStack stores 1
myStack.push('b');            // myStack stores 1 and 'b'
myStack.push(3);              // myStack stores 1, 'b', and 3
console.log(myStack.pop());   // logs 3
console.log(myStack.size());  // logs 2
{% endcoderay %}

# 4. Pseudoclassical Instantiation

This is the most commonly used class pattern. It's also the most complicated because, in addition to using the `this` keyword, it involves two concepts that the other class patterns don't require: the `new` keyword and prototypes. Prototypal instantiation uses prototypes via `Object.create()`, but pseudoclassical instantiation needs you to explicitly type out `ClassName.prototype.methodName`, which is just another source of confusion for beginners.

Also, it's the only class pattern that uses a true [constructor](http://en.wikipedia.org/wiki/Constructor_(object-oriented_programming)) for creating new instances. Other class patterns use instantiator functions that explicitly return a new instance. The pseudoclassical class pattern does not perform such a return thanks to the `new` keyword.

#### Characteristics

- Uses prototype chains to provide methods to instances of a class.
- Allows for dynamic method modification and inheritance (subclasses!) via prototype chains.
- Refers to the instance that's being created with the `this` keyword.
- Needs the `new` keyword to make an instance of a class.
- Has a true constructor that is named with a noun rather than a verb. The name is capitalized.
- Is the most commonly used class pattern.

#### Example code:
{% coderay Queue from scratch (pseudoclassical instantiation) lang:javascript %}
// Class name is now a noun (no verb), and it starts with an upper case letter
var Queue = function(queueName, comment){
  // Notice the use of 'this'
  this.name = queueName,
  this.annotation = comment,
  this.head: 0,
  this.tail: 0,
  this.storage: {}
};

// Notice the use of 'prototype'
Queue.prototype.enqueue = function(data){
  this.storage[this.tail] = data;
  this.tail++;
};
Queue.prototype.dequeue = function(){
  if(this.head <= this.tail){
    var data = this.storage[this.head];
    delete this.storage[this.head];
    this.head++;
    return data;
  }
};
Queue.prototype.size = function(){
  return this.tail - this.head;
};

// Create an instance of the Stack class by using the 'new' keyword:
var myCoolQueue = new Queue("Jeff's Queue","The grass is always greener, but just as hard to mowww!");
// Use the instance just like in previous examples
myCoolQueue.enqueue('a');             // myCoolQueue stores 'a'
myCoolQueue.enqueue(2);               // myCoolQueue stores 'a' and 2
myCoolQueue.enqueue('c');             // myCoolQueue stores 'a', 2, and 'c'
console.log(myCoolQueue.dequeue());   // output: 'a'
console.log(myCoolQueue.size());      // output: 2
{% endcoderay %}
