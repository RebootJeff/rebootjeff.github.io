---
layout: post
title: "New Awesomeness Added: Auto HR after H1"
date: 2013-08-15 12:02
comments: true
categories: ['CSS','blog customization','TIL','markdown']
---

I wasn't happy with the style of my standard `<h1>` header. I wanted to spice things up. After some aimless browsing, I learned that there is an `:after` selector in CSS. Inspired by this new selector, I wanted to find a way to add an `<hr/>` element "after" my `<h1>` headers. 

# Check Out This Sweet HR, Man

Apparently, it doesn't quite work the way I expected, but that's ok because I eventually found [this sweet compilation of horizontal rules](http://css-tricks.com/examples/hrs/)!

I entered the following CSS code into my **sass/custom/\_styles.scss** file:

~~~
.entry-content h1 {
  text-align: center;
  margin-top: 12px;
}
.entry-content h1:after {
  content: " ";
  display: block;
  height: 1px;
  margin: 6px 0px 6px 0px;
  background-image: -webkit-linear-gradient(left, rgba(0,0,0,0), rgba(0,0,0,0.75), rgba(0,0,0,0)); 
  background-image:    -moz-linear-gradient(left, rgba(0,0,0,0), rgba(0,0,0,0.75), rgba(0,0,0,0)); 
  background-image:     -ms-linear-gradient(left, rgba(0,0,0,0), rgba(0,0,0,0.75), rgba(0,0,0,0)); 
  background-image:      -o-linear-gradient(left, rgba(0,0,0,0), rgba(0,0,0,0.75), rgba(0,0,0,0)); 
}
~~~
{:lang="css"}

So instead of adding `<hr/>`s after my `<h1>`s, I added gradients inside of very thin background images. It's more complicated than what I had originally envisioned, but it looks way nicer.

# Codeblock, the Party Pooper
Unfortunately, in the process of writing this blog post, I discovered that my codeblocks (powered by CodeRay) aren't as responsive as I had hoped. I mentioned my CodeRay configuration in [my first post](/blog/2013/08/02/ready-set-octopress/#update-aug-10-2013). The configuration involves picking a codeblock format Octopress **\_config.yml** file.

I chose `coderay_line_numbers: table` at first, because I want line numbers, and I want them to be separated from the code. The problem is that CodeRay codeblock tables are apparently unresponsive to browser size. Consequently, the codeblocks were wider than the `<div>`s that contained them whenever they were viewed on a smartphone or even on a PC looking at this blog's front page. The front page automatically narrows my posts quite a bit, and that made the codeblock tables very unhappy. It was very annoying.

I haven't found a true solution despite diving into the CSS. All the relevant CSS selectors already have `width: 100%` so I don't know what else to do. I experimented with some `overflow` properties, but to no avail. For now, I have resorted to turning off line numbers entirely. Dammit.