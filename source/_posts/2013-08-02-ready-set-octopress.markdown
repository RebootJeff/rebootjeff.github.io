---
layout: post
title: "Ready. Set. Octopress."
date: 2013-08-02 17:40
comments: true
categories: octopress blogging about markdown
---

#Here We Go
Dammit. I've made so many tweaks and adjustments, but I still haven't gotten this blog looking quite right. I'm about to get geeky, so [jump down](#whats-next).

FYI, I'm using [Octopress](http://octopress.org) to create this blog, [github](https://github.com/RebootJeff) to host, and I write posts/pages in a little language called [Markdown](http://daringfireball.net/projects/Markdown/). Maybe I should've just created a wordpress blog, but I admit I fell victim to Octopress's tagline: "A blogging framework for hackers."

Some of you non-tech geeks may raise an eyebrow at the term "[hacker](http://www.paulgraham.com/gba.html)," but it's really not as evil as you think. The word embodies a more jargon-y connotation as well as the archetype portrayed in the media. In this case, Octopress is appealing to the techy DIY folks who like to have a lot of control over their creations (even at the expense of convenience...as is definitely the case for me).

##The Tweaks Never End
I began customizing this blog by adding a lovely Octopress theme. I then tweaked the hell out of it. You can compare and contrast by checking out the theme's [original implementation](http://www.adrianartiles.com/). Changes include changing the color scheme, the background image, the size of the hero (i.e., cover photo area), the Twitter widget, the footer, navigation links, etc.

The customization process was tough because I had never seen a [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) setup before. Also, I'm fairly new to git, Ruby, and the other bits involved in an Octopress-powered blog. I had to delete, re-install, and re-clone more times than I care to disclose.

But I'm still not done. I still need to tweak the colors and the background image. I want a green theme because I think green is under-used. Unfortunately, it clashes with certain Markdown parts. I switched my blog's Markdown engine to [Redcarpet](https://github.com/vmg/redcarpet), but I still get gross code blocks and lists. I tried using [a plugin](https://github.com/nono/Jekyll-plugins/blob/master/redcarpet2_markdown.rb), but that threw errors during the `rake generation` process.

Here are a few examples of the grossness I'm talking about:
	1. Why is this list
	2. such a clashy color?
and
```javascript
if thisCodeBlock == "ugly" then{
	console.log("dammit");
}
```

#TL;DR
I'm whining about how difficult it can be to use a DIY path, but it's really helped me learn a lot. So it's all good.

##What's Next?<a id="whats-next"></a>
So what can you expect on this blog other than sentences that probably shouldn't start with the word "so"?

###Past
- Difficulties of my cross-country move

###Present
- Chronicles of my career change
- Short reviews
- Compilations of cool links I've found

###Future
- My goals, targets, milestones
- My thoughts on the future of tech, cars, gaming, music, tennis, and more