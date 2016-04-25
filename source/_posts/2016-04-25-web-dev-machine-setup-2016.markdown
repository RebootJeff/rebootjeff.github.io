---
layout: post
title: "Web Dev Machine Setup 2016"
date: 2016-04-25 19:04
comments: true
categories:
  - 'dev tools'
  - 'software development'
  - 'web development'
---
# My Web Dev Setup

It's been nearly two years since I wrote about [my preferences for Sublime Text 2](http://rebootjeff.github.io/blog/2014/05/15/my-sublime-text-2-setup-and-customization/). In those two years, I've accrued more tools, and I've installed/configured a better web dev setup for myself. **_My current setup is [documented in a repo](https://github.com/RebootJeff/my-installfest)_**, which will be kept up to date so then any time I need to set up a new machine, I have a quick guide that I can reference.

There are a few aspects of my setup worth explaining...

## Atom vs Sublime Text

I've switched to Atom. There's no doubt that Sublime Text is way faster. I still use it to read and edit extremely large files (e.g., large JSON). But Sublime Text always felt a bit clunky in its GUI. Most notably, the package manager for Sublime Text wasn't very nice to use.

On Macs, Atom has a lot of great features for updating the software and packages. It has one-click installation of shell commands (e.g., `atom [filename]` to open a file in Atom via terminal).

On Linux, these features are missing, but I still use Atom on my Ubuntu machine because its GUI feels more modern than Sublime Text's GUI. Also, Atom's built-in Markdown and Git features are pretty sweet.

That said, [Microsoft's Visual Code Studio](https://code.visualstudio.com/) looks enticing. The battle of free code editors is really heating up! Visual Code Studio appears to be more powerful than Atom -- and I've got to give it a try eventually -- but Atom's community is at least 2x larger at the moment. The ecosystem of Atom packages is outstanding.

Some of my favorite Atom packages:
- [pigments](https://atom.io/packages/pigments) to highlight colors (great for CSS/SCSS/LESS code that deal with colors)
- [file-icons](https://atom.io/packages/file-icons) to show icons specific to different file types
- [autocomplete-emojis](https://atom.io/packages/autocomplete-emojis) because emojis can spice up any comment/documentation! 🌟

![Atom screenshot](/images/20160425/atom_ss.png)

## Browsers

### A few words about Chrome

I still use Google Chrome as my main browser for development, and now I use a few Chrome extensions a whole lot: [Advanced REST Client](https://chrome.google.com/webstore/detail/advanced-rest-client/hgmloofddffdnphfgcellkdfbfbjeloo?hl=en-US) for testing REST APIs and [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc/related?hl=en) for browsing JSON data.

For development, it can be helpful to disable the "prefetch resources" advanced setting. If it's enabled, the network panel of your Chrome DevTools might jump the gun, confusing you in the process.

### Firefox is getting better

That said, I'm enjoying [Mozilla Firefox Developer Edition](https://www.mozilla.org/en-US/firefox/developer/). It's got some [fancy dev tools](https://www.youtube.com/playlist?list=PLo3w8EB99pqLRJBWRCoyGTIrkctoUgB9W) that I haven't gotten a chance to use much, but the browser itself feels pretty speedy. Unlike normal Firefox, the dev edition has separate processes for each tab.

#### Mini-Rant: Modern Browser Wars

Also, I like supporting Mozilla by using their browser. [It's good to have some competition in browsers](https://www.youtube.com/watch?v=_YkTAu333xM), and Mozilla has no conflict of interest with the web. They're more likely to promote an open web as much as possible whereas Google and especially Apple have a conflict of supporting web versus supporting iOS/Android apps. [Some say Safari is neglected](http://arstechnica.com/information-technology/2015/06/op-ed-safari-is-the-new-internet-explorer/) by Apple because they care more about dedicating resources to iOS + the App Store.

There's also a nice conspiracy theory suggesting that Apple would rather web apps not rise in popularity because that would detract from the App Store's prominence. You could argue the same goes for Google and the Play store, but Google's done some amazing work on "[Progressive Web Apps](https://developers.google.com/web/progressive-web-apps)" to make web tech (push notifications, offline support, etc) as powerful as native mobile apps.

## Mac Tips & Tricks

[My documentation repo](https://github.com/RebootJeff/my-installfest) has more tips & tricks, but I'll lay out a few here. They all happen to relate to making development on a Mac even better (I guess I've been using my Mac way more than my Ubuntu machine lately).

#### Window Management
The latest Mac OSX has a built-in window layout feature, but it sucks. I continue to use [SizeUp](http://www.irradiatedsoftware.com/sizeup/). It's free and more powerful/flexible.

#### Installing software on Macs
I try to install as much as possible via [Homebrew](http://brew.sh/). It makes updating installed software a bit easier, and it can help you avoid common pitfalls (e.g., installing Node.js via Homebrew avoids permissions issues with `npm install -g` that you'd normally have to fix yourself).

#### Horrible "Smart Quotes"
Do yourself a favor and go into the keyboard settings to disable Smart Quotes. Otherwise, they could eventually find their way into your code and screw you up in the most insidious way (it could take awhile for you to realize you've accidentally typed/copy/pasted some Smart Quotes into your code).
