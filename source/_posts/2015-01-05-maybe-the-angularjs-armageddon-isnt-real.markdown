---
layout: post
title: "The Myth of the AngularJS Armageddon"
date: 2015-01-05 19:26
comments: true
categories:
  - AngularJS
  - JavaScript
  - technical posts
---

![RIP? AngularJS](/images/20150105/AngularRIP.png)

A few months ago, the JavaScript community had a rather negative [reaction to an announcement about Angular v2.0](https://www.quora.com/Why-are-many-developers-upset-about-the-changes-in-Angular-2-0). *Quick aside: my boss lost faith in Google and jumped on the ReactJS bandwagon.* On a [recent episode](http://devchat.tv/adventures-in-angular/016-aia-ng-1-3-and-2-0-with-brad-green-igor-minar-and-mi-ko-hevery) of the Adventures in Angular podcast, the Angular core dev team tried to clear the air regarding the general approach for Angular 2.0 and the differences between Angular 1.3 and 2.0. The podcast is surprisingly well-done. There are 9 people included (1 of them is THE [John Papa](http://www.johnpapa.net/angularjs-patterns-clean-code-released/); 4 of them are Angular team members) and yet they never accidentally interrupt one another or talk over one another.

I've listed some interesting bits I gleaned:

### Some Misunderstandings

- It sounds like there might actually be a migration path for 1.3 to 2.0. There is no path yet because 2.0 isn't close enough to completion to judge. The idea of **"no migration path" was a misunderstanding**.
- It is not necessary to use AtScript for Angular 2.0 (and it is not necessary to use Angular 2.0 for AtScript).

### Some Rationale

- They're trying to re-make their routing module in a way that will be easier to use.
- Some things are disappearing for logical reasons:
    - `$scope` is disappearing because they realized "controller as" syntax is best, so they want to revamp that system completely to avoid common `$scope` confusion.
    - Code for directives will be totally different because [Directive Definition Objects](https://d2eip9sf3oo6c2.cloudfront.net/pdf/egghead-io-directive-definition-object-cheat-sheet.pdf) as they currently stand are ugly and kind of convoluted (e.g., most directives don't need a linking function, they just need a controller function --kind of like how most views/templates should use `controllerAs` instead of `$scope`).
    - Angular's module system will disappear because ECMAScript6 will have a native module system. By embracing the new ES6 system, it will make Angular 2.0 more compatible with future non-Angular modules (much like how all back-end JS embraces Node's system).
- There are a few **key motivations behind Angular 2.0's design:**
    - Mobile friendliness.
    - Fixing mistakes they've made when creating Angular 1.x (e.g., getting rid of $scope).
    - Simplicity and performance.
    - Embracing future tech like ES6 and web components.

### Some Points of Emphasis

- The new syntax looks crazy, but the Angular team claims that it will be much harder to convert a non-Angular 1.3 app to 2.0 than to convert Angular 1.3 to 2.0 --which sounds like a no-brainer, but as you can imagine, they're really trying to emphasize that you should not abandon 1.3 just because 2.0 looks so different now.
- They emphasized how Angular 2.0 is still in a state of flux, so it's too early to make business decisions based on it.
- The Angular team claims they are making changes for practical reasons, not purely academic reasons. In other words, they have examined how current Angular apps are made, deployed, etc. They don't just think about what would be cool, they do think about what would be truly helpful/useful.

### My Takeaways

I know I sound like I'm defending the Angular team. To a certain extent, that's true (I need to try some React.js one day to hopefully reduce my bias for Angular), but it really comes down to:

- They're converting to ES6, which means it will probably be necessary to use a transpiler to convert core Angular 2.0 code to ES5 for older browsers.
  - Ideally, this won't be a huge problem for evergreen (self-updating) browsers. Maybe they will support key ES6 features by the time Angular 2.0 becomes "mainstream" (in the same sense that Angular 1.3 is currently "mainstream"). Or maybe I'm dreaming :p.
- There were some huge misunderstandings when Angular 2.0 was announced (re: lack of migration path, role of AtScript, etc).
- It's too early to really tell what Angular 2.0 will look like when it's released.
- When Angular 2.0 does arrive, it may look syntactically different, but it will do many of the same, *Angulary* things (i.e., the Angular "flavor" of MVC, augmenting HTML markup, enabling powerful custom components, etc).

### Newsflash! Angular 1.x is NOT Dead!

**Angular 1.4 is [coming in Spring 2015](http://angularjs.blogspot.com/2014/12/planning-angular-14.html).**

News of 1.4 landed *after* the podcast aired. It will bring the new router I mentioned earlier, a "first class" I18N system, slick-looking documentation (using [Angular-Material](https://material.angularjs.org/)), and other goodies --including some breaking changes. :D
