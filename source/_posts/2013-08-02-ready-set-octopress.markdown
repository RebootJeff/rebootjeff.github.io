---
layout: post
title: "Ready. Set. Octopress."
date: 2013-08-02 17:40
comments: true
categories: octopress blogging test-post
---

#Test

	1. This is a list.
		a. Hello
		b. Bye

>block quote
>stuff

```javascript
var hello = "hello";
var length = hello.length;
// This is a block of javascript code
```

![](http://ubuntugenius.files.wordpress.com/2012/06/pdf-open-with.png?w=500)

in line `code` here

**I wish block quotes, code blocks, etc. didn't look so dark and blue. How can I change these colors/styles?**
Changing from rdiscount to redcarpet markdown engine has helped with block quotes. The list and code block styles still clash with my blog's style. I tried to use the redcarpet2_markdown.rb plugin, but it causes `rake generate` to throw a fit.