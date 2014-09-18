---
layout: post
title: "Web Security Fundamentals - Part 1: What Google Peeps Say"
date: 2014-09-18 10:26
comments: true
categories:
  - web tech
  - security
  - technical posts
---

Back in late May, I went to one of the most informative tech meetups ever. The [SFHTML5 meetup group](http://www.meetup.com/sfhtml5/) organized an event at the Google SF office to cover web security. Google security researchers presented for about 2.5 hours of lectures talking about common hacks/attacks, good defense, the general state of web security, etc.

You can check out the slides here: [click here if you dare.](http://www.meetup.com/sfhtml5/events/179713932/#event_comment-362704742) You can watch the lectures here:

<iframe width="300" height="185" src="//www.youtube-nocookie.com/embed/Yg5g2aMKbNA?list=PLOU2XLYxmsIIkEU3Z_xdVo9EADurbdxKa" frameborder="0" allowfullscreen></iframe>
<p></p>

But if you don't feel like sitting through 2.5 hours of lecture, allow me to summarize the best parts:

1. Common hacks/exploits
  - XSS
  - CSRF
  - MITM
2. Simple security best practices
  - Use frameworks/libraries to fight XSS for you
  - Implement CSP on your server
  - Reinforce HTTPS with HSTS

**I won't go into detail about any particular topic.** This blog post will simply get you started in understanding fundamental web security. I suggest you use Google to research more about hacks/attacks or wait for me to post another blog post that provides a collection of links to sweet videos, references, and articles that I found particularly helpful for learning more about all these topics.

# Be Afraid

How are websites and web apps compromised? Why are sites often "hacked"? There are three main types of attacks that you should worry about: XSS, CSRF, and MITM.

## Cross-Site Scripting (XSS)

When a punk manages to get your code to run their JavaScript, that's XSS. A simple example is when an unprotected website just accepts text from the user and adds it to the site's HTML code. If that text is actually JS, then the site ends up sending the browser user-generated code. Damn.

XSS is one of the most common problems plaguing web security today. This is pretty depressing because there are plenty of frameworks and libraries that help fight XSS, but so many site operators just don't use them and some fools even try to write their own anti-XSS code.

## Cross-Site Request Forgery (XSRF/CSRF)

Let's say a user logs into your website or web app. They are now authenticated, right? Well it depends. It could be that the user's *browser* is authenticated. An attacker could take advantage of this authentication and get the user's browser to submit an HTTP request crafted with nefarious intentions. The request will be accepted because the browser has the right authentication cookie data, for example.

How is the evil HTTP request initiated? It could be through XSS, it could be through convincing a victim to visit a malicious site that sends HTTP requests, etc. Most examples mention authenticated cookies being used by attackers.

## Man-in-the-Middle (MITM)

There's a reason why public internet is unsafe. When you're on a shared network, other users on the same network can try to intercept your data. Not only can man-in-the-middle attacks read your data, they can also send you bad data/code. Some attackers merely intercept web pages you're accessing, add more advertisements, and feed you the web page with extra ads. Other attackers might intercept your attempt to visit http://www.facebook.com, give you a fake Facebook login page, and convince you to submit your login info to them.

Obviously, protecting a network by requiring a password to connect can help. However, if you're using public WiFi in a coffee shop where the password is given to anybody who asks for it, then you're in trouble again. As I shall mention, HTTPS is crucial for fighting MITM pain.

# Be Somewhat Less Afraid

It's great if you're aware of threats. Now it's time to learn the basics on how to combat the threats. At the meetup, the Google peeps focused on three types of solutions: frameworks/libraries, CSP, and HTTPS with HSTS. I will also mention a couple other technologies (BONUS) for your consideration.

## Frameworks/Libraries Features

One of the Google experts emphasized that XSS is a much bigger problem than it should be because there are so many frameworks and libraries that help fight XSS. He said that no one should be writing their own anti-XSS libraries. Instead, use one of the many open-source solutions. Also, it's quite possible that you're already using a framework that has anti-XSS features that just need to be activated or configured.

For example, in some templating libraries, a simple syntax change will enable anti-XSS escaping features. Other templating libraries automatically escape contents by default. Some frameworks like AngularJS do "round-trip escaping on all strings for you" to protect your app from XSS and other injection attacks.

## Content Security Policy (CSP)

A server can instruct a browser to use a whitelist to decide which resources should be loaded and which should be blocked. This is done when a server adds a CSP to a response header.

For example, a CSP whitelist can tell a browser to trust script files from the server and Google CDNs, images from the server and Amazon CDNs, CSS files from the server, and web fonts from Google. Everything else will be blocked. In-line JavaScript will be blocked, in-line styles will be blocked, images hosted by 3rd parties will be blocked, Flash will be blocked, iframes will be blocked, etc.

Your CSP can be configured based on various types of resources. Check this [CSP Cheatsheet](http://content-security-policy.com/) for the list of options. I recommend that you investigate server-side libraries, frameworks, or middleware that can help you implement CSP. When writing your CSP, you can try starting with the most restrictive whitelist and then see what needs to be unblocked.

### Reporting Feature

You can also set up a reporting system to find out what your CSP has managed to block (thereby identifying failed attacks).

A Googler suggested using the CSP reporting feature *without* an enforced whitelist to help you examine what browsers are actually digesting when they visit your site or app. For example, you could set up a CSP that has a whitelist and just asks browsers to report non-whitelisted sources without actually blocking them. This gives you the ability to **tweak your whitelist based on production usage without changing production usage**. After you're done tweaking, change the CSP to force browsers to report *and* block uninvited resources and content.

{% coderay lang:JavaScript Ultra-Strict Example CSP for Express server using Lusca middleware %}
app.use(lusca.csp({
  policy: {
    'default-src': 'none', // Block EVERYTHING
  },
  reportOnly: true, // Record what's being blocked
  reportUri: '/report-violation-endpoint'
}));
{% endcoderay %}

## HTTPS and HTTPS Strict Transport Security (HSTS)

### HTTPS

To protect data transfers from MITM attacks, many sites connect to visitors via HTTPS. HTTPS connections not only protect typical payloads like JSON, but also static files and cookies that would otherwise be vulnerable to CSRF attacks. The hard part about using HTTPS is making sure no part of the site ever falls back to unencrypted HTTP.

For example, let's say you're browsing a site that provides free icons and graphics. Are all files served over HTTPS? HTML, CSS, and JavaScript files are no-brainers. What about images? Yeah that's pretty standard too. But what about when you get an icon pack? You click a download link, and the browser starts downloading a zip file. Is that using the HTTPS protocol? It's easy to [make mistakes](http://httpshaming.tumblr.com/).

### HSTS

Furthermore, what if a user visits the site using HTTP first? It's pretty common for people to type "somewebsite.com" in the URL bar and the browser will turn that into "http://somewebsite.com". After they visit that URL, the site can redirect the visitor to "**https**://somewebsite.com". But sadly, that initial connection via http wasn't secure. It's susceptible to a MITM attack.

With HTTPS Strict Transport Security, the browser can automatically turn "somewebsite.com" into "**https**://somewebsite.com". HSTS works by setting a header that tells the browser to enforce HTTPS for requests sent to the domain ("somewebsite.com") for the next X number of seconds. Yes, you can set X to be a very large number such that HSTS is enforcing HTTPS for the next *year*, if you want to be cool like that.

# Stay Tuned

This blog post was getting pretty lengthy, so I decided to split it into two parts. In a follow-up blog post, I will provide a list of references, tutorials, and videos to help you research more about CSP, HSTS, and some complementary tools/libraries.
