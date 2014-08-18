---
layout: post
title: "My Sublime Text 2 Setup and Customization"
date: 2014-05-15 20:32
comments: true
categories: ['dev tools', 'customization', 'software development']
---

*Updated on August 8, 2014.*

I use Sublime Text 2 as my text editor for coding. I don't use a fancy IDE like WebStorm, but I do plan on trying out WebStorm more at work. Actually, I should probably upgrade to ST3, but for now, I'm happy with ST2.

# Config

However, ST2's light weight comes at a cost: you probably need to configure some stuff before you're really ready to roll. Here's what I do when I first install ST2 on a machine.

## Key Bindings

First, I change the keyboard shortcuts for cycling through open tabs. The default behavior is based on your usage history (most recently viewed tabs), but I prefer just cycling from left to right. Therefore, I edited my key bindings like so...

{% coderay lang:json Preferences > Key Bindings – User %}
{ "keys": ["ctrl+tab"], "command": "next_view" },
{ "keys": ["ctrl+shift+tab"], "command": "prev_view" },
{% endcoderay %}

## Settings

Next up, I make sure my whitespace is configured to my liking. I think most coders who lift hefty amounts of JavaScript go with indentation 2 spaces at a time, so that's what I do. I prefer it because it takes up less space than a typical 4-space tab, which is critical when viewing code in split-screen mode. I also like having the option to manually change indentation with spaces if necessary for alignment purposes. Mixing spaces and tabs gets messy.

I also configure Sublime Text to automatically add a new line at the end of every file whenever I save. It won't add a new line if one already exists at EOF. I personally never suffer from lack of new line at EOF, but [some UNIX tools won't work without them](http://stackoverflow.com/questions/729692/why-should-files-end-with-a-newline), and I know lots of hardcore coders out there like using such tools. I don't want to screw them over. With that said, allow me to present my ST2 settings...

{% coderay lang:js Preferences > Settings – User %}
// The number of spaces a tab is considered equal to
  "tab_size": 2,

 // Set to true to insert spaces when tab is pressed
  "translate_tabs_to_spaces": true,

// Set to true to ensure the last line of the file ends in a newline
// character when saving
  "ensure_newline_at_eof_on_save": true,
{% endcoderay %}

# Theme (UI Skin)

I use the Nexus theme, which you can find here: [https://github.com/EleazarCrusader/nexus-theme](https://github.com/EleazarCrusader/nexus-theme). The readme file explains a bunch of different installation options, but I recommend installing via Package Manager. The readme also tells you how to activate the theme after installation.

![official Nexus theme screenshot](https://raw.githubusercontent.com/EleazarCrusader/nexus-theme/master/nexus-theme.png)

<p class="my-caption">The orange and blue decorations on the tabs tell you if the file has been change since last save.</p>

# Packages

Sublime Text doesn't come with many bells and whistles. Instead you add them as packages. First, you must install the package manager by following [these instructions](https://sublime.wbond.net/installation#st2). After that, get ready to discover a giant pool of all the bells and whistles you could possibly want. If you need to adjust the settings for any of these packages, you can usually find good documentation from the readme files of their respective GitHub repos.

After you install Package Manager, you can access it by hitting `Ctrl+Shift+P` (or perhaps `Cmd+Shift+P` for Macs?) and then typing "package control" into the search box. The typeahead will reveal your various options, but you mostly be using "Package Control: Install Package". There will be some load time necessary to provide you a list of available packages, but after it's done, you can search for packages by name. Installation will similarly require some load time. Check the bottom-left of the ST2 window to see relevant status messages.

Here are the packages I installed:

### Alignment
Prettify your code by aligning multiple lines of variable definitions and hash objects. For example...

{% coderay lang:js Before and After using the Alignment package %}
// this stuff...
var x = 123;
var foo = 'bar';
var exampleObj = {
  my: x,
  name: 99,
  is: 'Jeff'
};

// would turn into this stuff...
var x          = 123;
var foo        = 'bar';
var exampleObj = {
  my  : x,
  name: 99,
  is  : 'Jeff'
};
{% endcoderay %}

This may look stupid to you, but I don't use it all the time. The main place I like to use it is with multiple `var example = require('npm package name here');` statements at the top of a JS file. By the way, I had to edit the package settings to get alignment for object literals. I added the `":"` seen below...

{% coderay lang:js Preferences > Package Settings > Alignment > Settings – User %}
{
  // The mid-line characters to align in a multi-line selection, changing
  // this to an empty array will disable mid-line alignment
  "alignment_chars": ["=", ":"]
}
{% endcoderay %}

### GitGutter
Add indicators in your gutter so then you can see which lines of code have been changed since the last git commit. See the left edge of this screenshot:
![GitGutter in action](http://i.imgur.com/ur6FY.png)

### SublimeLinter
I prefer live linting over build-time linting. SublimeLinter supports a ton of languages, and I have it set to simply bring up an indicator in the gutter and some underscores to point to any issues it finds. It's not too obtrusive.

### TrailingSpaces
Extraneous whitespace is bad. Trailing whitespace is worse. I use this package to highlight any trailing whitespace in bright pink. I bet I could set my linter to do this, but oh well.

### MarkdownEditing
Who doesn't love Markdown? It makes GitHub README files and wiki pages look great. It makes dev blogs look great. It makes writing dev-related text easy. Sometimes, I write rough drafts of blog posts within Google Docs or [Dillinger](http://dillinger.io/), which is a sweet online Markdown editor. In the end, I always complete my blog posts by writing Markdown within Sublime Text.

I recently found a sweet ST package to help edit Markdown files: MarkdownEditing. It completely transforms the look and syntax highlighting of your Markdown. Sadly, I use CodeRay for codeblocks rather than standard Markdown markup. So MarkdownEditing can't beautify my codeblocks within Sublime Text, but `inline code snippets like this one` are highlighted in a very helpful way. You can see all the ways that the package alters your Markdown [here](https://camo.githubusercontent.com/35a66d68a55666133ba7911fb0ea61277740680f/68747470733a2f2f7261772e6769746875622e636f6d2f5375626c696d65546578742d4d61726b646f776e2f4d61726b646f776e45646974696e672f6d61737465722f73637265656e73686f74732f6c696768742e706e67). Keep in mind that there are a couple other themes available specifically for MarkdownEditing. I use the dark theme of course.

## Syntax

You might also find it handy to install packages for specific languages. For example, I dabble with CSS pre-processors and templating languages. I'm currently checking out LESS for CSS and Jade for HTML, so I've installed syntax highlighters for them. The package names are simply "LESS" and "Jade".
