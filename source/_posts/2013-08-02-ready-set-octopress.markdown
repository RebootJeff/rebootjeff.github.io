---
layout: post
title: "Ready. Set. Octopress."
date: 2013-08-02 17:40
comments: true
categories: octopress blogging about markdown
---

<p class="last-updated">Last updated: Aug 10th, 2013</p>

#Here We Go
Dammit. I've made so many tweaks and adjustments, but I still haven't gotten this blog looking quite right. I'm about to get nerdy, so [jump down](#whats-next) if you have no sympathy for programmer growing pains.

FYI, I'm using [Octopress](http://octopress.org) to create this blog, [github](https://github.com/RebootJeff) to host, and I write posts/pages in a little language called [Markdown](http://daringfireball.net/projects/Markdown/). Maybe I should've just created a WordPress blog, but I admit I fell victim to Octopress's tagline: "A blogging framework for hackers."

Some of you non-tech geeks may raise an eyebrow at the term "hacker," but it's really [not as evil as you think](http://www.paulgraham.com/gba.html). The word embodies a more jargon-y connotation as well as the archetype portrayed in the media. In this case, Octopress is appealing to the techy DIY folks who like to have a lot of control over their creations (even at the expense of convenience...as is definitely the case for me).

##The Tweaks Never End
I began customizing this blog by adding a lovely Octopress theme. I then tweaked the hell out of it. You can compare and contrast by checking out the theme's [original implementation](http://www.adrianartiles.com/). My changes customized the color scheme, the background image, the size of the hero (i.e., cover photo area on the home page), the Twitter widget, the footer, navigation links, etc.

The customization process was tough because I had never seen a [Liquid](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) setup before. Also, I'm fairly new to git, Ruby, and the other bits involved in an Octopress-powered blog. I had to delete, re-install, and re-clone more times than I care to disclose.

<del>But I'm still not done. I still need to tweak the colors and the background image. I want a green theme because I think green is under-used. Unfortunately, it clashes with certain Markdown parts. I switched my blog's Markdown engine to [Redcarpet](https://github.com/vmg/redcarpet), but I still get gross code blocks and lists. I tried using [a Redcarpet plugin](https://github.com/nono/Jekyll-plugins/blob/master/redcarpet2_markdown.rb), but that threw errors during the `rake generate` process. I tried [kramdown](http://blog.alestanis.com/2013/02/04/octopress-and-the-twilight-color-scheme/) with a sweet [CodeRay theme](https://github.com/danielpietzsch/CodeRay-GitHub-Theme), but that setup completely ignored code blocks, block quotes, etc. I need help!</del>

###Update! (Aug 10, 2013)
I used [HTML5 Dev Gal](http://html5devgal.com/blog/2013/06/08/octopress-toc-and-coderay-codeblocks/)'s helpful instructions and links to finally implement the alliterative combo of Kramdown and CodeRay. I also realized how to add custom CSS to specifically address lists created via the Markdown engine.

So hooray! Lists and Code blocks are no longer given a ridiculous dark blue background! And why were lists given a background anyway?

Sadly, [automatic TOCs](http://kramdown.rubyforge.org/converter/html.html#toc) don't seem to work. I also still need to figure out how to add autolinking, which works in stock Octopress, but once modified to use kramdown, shit's broken?

#TL;DR
I'm whining about how difficult it can be to use a DIY path, but it's really helped me learn a lot. So it's all good.

##What's Next?
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