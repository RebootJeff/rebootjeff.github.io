---
layout: post
title: "My Sublime Text 2 Setup and Customization"
date: 2014-05-15 20:32
comments: true
categories: 
---

# Config

## Key Bindings
{% coderay lang:json Preferences -> Key Bindings - Default %}
{ "keys": ["ctrl+tab"], "command": "next_view" },
{ "keys": ["ctrl+shift+tab"], "command": "prev_view" },
{% endcoderay %}

## Settings
{% coderay lang:js Preferences -> Settings - Default %}
// The number of spaces a tab is considered equal to
  "tab_size": 2,

 // Set to true to insert spaces when tab is pressed
  "translate_tabs_to_spaces": true,

// Set to true to ensure the last line of the file ends in a newline
// character when saving
  "ensure_newline_at_eof_on_save": true,
{% endcoderay %}

# Skin

https://github.com/EleazarCrusader/nexus-theme

# Packages

- Alignment
- GitGutter
- SublimeLinter
- TrailingSpaces

## Syntax

- LESS
- Jade
