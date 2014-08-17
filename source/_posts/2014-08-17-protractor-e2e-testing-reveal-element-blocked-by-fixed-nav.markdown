---
layout: post
title: "Protractor E2E Testing: Reveal Element Blocked By Fixed Nav"
date: 2014-08-17 14:19
comments: true
categories:
  - Protractor
  - E2E testing
  - Learned On The Job
  - AngularJS
  - technical posts
---

End-to-end testing can be pretty tricky. There are a lot of "gotchas" that prove how hard it can be for you to truly think from the perspective of a computer. Ideally, E2E testing is all about writing tests from the perspective of a user, but that's not going to always provide smooth sailing when writing E2E spec files.

This blog post is going to focus on a gotcha that rears its ugly head when you have a fixed nav bar. Nowadays, it's pretty common to see fixed nav bars. Let's use Twitter as an example. Twitter doesn't use Angular, so you wouldn't want to test their site using Protractor, but what I'm about to talk about also applies to WebDriver (which can be used for any site running on any tech).

![Twitter nav bar blocking an avatar](/images/20140817/screenshot_twitter_fixed_nav.png)

# What's the big deal?

Here's the problem: **what if we want Protractor to click on the avatar under the fixed nav bar as seen in the screenshot above?**

{% coderay lang:JavaScript Example A - E2E spec with potential problem %}
describe('"Who to Follow" widget', function() {
  it('should include avatars that go to other Twitter profiles', function() {
    // get first (index 0) avatar using class-based CSS selector
    var avatar = $$('.who-to-follow .avatar').get(0);

    // Will this click always work?
    avatar.click();

    // assertion of what to expect as a result of the click
    expect(blahBlahBlah).toBe(yadaYada);
  });
});
{% endcoderay %}

When you use `.click()`, you might expect Protractor (or WebDriver, which serves as the underlying engine for Protractor) will try to scroll the web page until the target element is displayed before clicking. However, Protractor will only scroll until the target element is in the browser *viewport*.

Now imagine your test suite includes several tests (ooh la la!). In test #1, the actions of the test cause Protractor to scroll to the bottom of the page. In test #2, the test tries to perform the actions of *Example A*. Therefore, during test #2, protractor tries to scroll back up the page until the target avatar is in the viewport, but this just brings the avatar directly under the fixed nav bar. Then Protractor attempts a click by finding the center of the target. So even if a tiny portion of the avatar's butt is displayed just below the bottom of the fixed nav bar, it won't be clicked. Instead, Protractor will throw an error saying that the target could not be clicked. The error will also mention that the nav bar would receive the click event.

# Well that sucks. Now what?

There are two main solutions to consider:

1. Un-fix the nav bar for your E2E tests. --Bleh!
2. Add extra scrolling to your E2E tests. --Okay

The first solution might not be a great idea because it's a major alteration for the sake of testing. What if the fixed position of the nav bar causes other issues that your tests will reveal? I believe you want E2E tests to interact with a product that is very close to the product users will interact with. Changing the nav bar's position just for testing goes against this philosophy. The main exception to this rule is animation: I believe it's ok to disable animations for E2E testing just because it can take up a lot of time, slowing down your test/build process. Also, animations can just be very cumbersome for automated E2E systems like Protractor to deal with.

## Solution: How to add pre-click scrolling

The solution I use for dealing with fixed nav bars is to define and use a helper function that invokes `element.scrollIntoView(false)`. This method is a native DOM element method [that you can read about on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element.scrollIntoView). You can't simply invoke it on a Protractor ElementFinder object. You can't call `elemFinder.scrollIntoView()` the same way you call `elemFinder.click()`.

Also, you may have noticed that `false` is passed into `scrollIntoView`. This tells the browser to scroll as far as it can in an attempt to align the bottom of the target element with the bottom of the scroll area. In other words, **this solution only solves issues with fixed nav bars at the *top* of the viewport.** Using `element.scrollIntoView(false)` will fail if your web app uses a fixed nav bar at the *bottom* of the viewport.

{% coderay lang:JavaScript Example B - Solution: Helper function to align element with bottom of viewport %}
// Inside a separate JS file that contains helper functions...

// Syntax Option 1
function scrollElemToBottomOfView(elem) {
  elem.scrollIntoView(false);
}
module.exports.scrollElemFinderIntoView = function(elemFinder) {
  var promise = browser.executeScript(scrollElemToBottomOfView, elemFinder);
  return promise;
};

// Syntax Option 2
module.exports.scrollElemFinderIntoView = function(elemFinder) {
  var promise = browser.executeScript(function(elem) {
    elem.scrollIntoView(false);
  }, elemFinder);
  return promise;
};

// Syntax Option 3
module.exports.scrollElemFinderIntoView = function(elemFinder) {
  var promise = browser.executeScript('arguments[0].scrollIntoView(false)', elemFinder);
  return promise;
};
{% endcoderay %}

There are 3 syntax options above because I just wanted to present a few different coding styles. As you can probably tell, `browser.executeScript()` accepts a couple of parameters. The first one is the script, the second one is the script's parameter. The script can either be a function (technically speaking, it's a function reference) or a string representation of the script's body. Syntax Option #3 was inspired by a Stack Overflow answer for a very similar situation (it was for WebDriver, but it was easy to translate to Protractor).

{% coderay lang:JavaScript Example C - Using the Solution %}
// Somewhere inside test code...
var helpers = require('../path/to/helpers');
helpers.scrollElemFinderIntoView(avatar);
avatar.click();
{% endcoderay %}

You may have noticed that the solution in *Example B* mentions promises, but the code in *Example C* does not use them. My understanding is that it's not crucial to use every single promise that Protractor and WebDriverJS provide. For example, even though the `click()` method returns a promise, you don't see devs writing Protractor tests with `exampleButton.click().then(function() { ... });` all the time.

So why did I mention promises in *Example B*? Just to reinforce the fact that `browser.executeScript()` will return a promise. By storing the result of `browser.executeScript()` in a variable called "promise", it tells other devs what to expect. That said, I admit it may not be terribly valuable. Let me know your opinion on this or any other part of the solution presented here.
