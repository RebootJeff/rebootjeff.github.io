---
layout: post
title: "Web Security Fundamentals by Google Peeps"
date: 2014-08-20 19:26
comments: true
categories:
  - web tech
  - security
  - technical posts
---

Back in late May, I went to one of the most informative tech meetups ever. The SFHTML5 meetup group organized an event at the Google SF office to cover web security. Google security researchers presented for about 2.5 hours of lectures talking about common hacks/attacks, good defense, the general state of web security, etc.

You can check out the slides here: [click here if you dare.](http://www.meetup.com/sfhtml5/events/179713932/#event_comment-362704742) You can watch the lectures here:

<iframe width="300" height="185" src="//www.youtube-nocookie.com/embed/Yg5g2aMKbNA?list=PLOU2XLYxmsIIkEU3Z_xdVo9EADurbdxKa" frameborder="0" allowfullscreen></iframe>


But if you don't feel like sitting through 2.5 hours of lecture, allow me to summarize the best parts:

1. Common hacks/exploits
  - XSS
  - CSRF
  - Man-in-the-Middle
2. Simple security best practices
  - Use frameworks/libraries to fight XSS for you
  - CSP
  - HTTPS + HSTS
3. Practices not mentioned
  - JWT

**I won't go into detail about any particular sub-topic.** This blog post will simply get you started in understanding fundamental web security. I suggest you use Google to research more about hacks/attacks and click provided links to learn more about solutions and best practices.

# Oh Noes!

## Cross-Site Scripting (XSS)

When a punk manages to get your code to run their JavaScript, that's XSS. A simple example is when an unprotected website just accepts text from the user and adds it to the site's HTML code. If that text is actually JS, then the site ends up sending the browser user-generated code. Damn.

XSS is one of the most common problems plaguing web security today. This is pretty depressing because there are plenty of frameworks and libraries that help fight XSS, but so many site operators just don't use them and some fools even try to write their own anti-XSS code.

## Cross-Site Request Forgery (XSRF/CSRF)

Let's say a user logs into your website or web app. They are now authenticated, right? Well it depends. It could be that the user's *browser* is authenticated. An attacker could take advantage of this authentication and get the user's browser to submit an HTTP request crafted with nefarious intentions. The request will be accepted because the browser has the right authentication cookie data, for example.

How is the evil HTTP request initiated? It could be through XSS, it could be through convincing a victim to visit a malicious site that sends HTTP requests, etc. Most examples mention authenticated cookies being used by attackers.

## Man-in-the-Middle

There's a reason why public internet is unsafe. When you're on a shared network, other users on the same network can try to intercept your data. Not only can man-in-the-middle attacks read your data, they can also send you bad data/code. Some attackers merely intercept web pages you're accessing, add more advertisements, and feed you the web page with extra ads. Other attackers might intercept your attempt to visit Facebook.com, give you a fake Facebook.com login page, and convince you to submit your login info to them.

Obviously, protecting a network by requiring a password to connect can help. However, if you're using public WiFi in a coffee shop where the password is given to anybody who asks for it, then you're in trouble again. As I shall mention, HTTPS is crucial for fighting man-in-the-middle pain.

# Oh Yeaaah

## Frameworks/Libraries Work Wonders

### Further Reading


## Content Security Policy (CSP)

### References

http://www.html5rocks.com/en/tutorials/security/content-security-policy/
https://developer.mozilla.org/en-US/docs/Web/Security/CSP
http://en.wikipedia.org/wiki/Content_Security_Policy
https://www.youtube.com/watch?v=pocsv39pNXA -- I highly recommend
http://content-security-policy.com/ -- Quick list of options

## HTTPS and HTTPS Strict Transport Security (HSTS)

https://www.leviathansecurity.com/blog/the-double-edged-sword-of-hsts-persistence-and-privacy/

### References

https://www.youtube.com/watch?v=zEV3HOuM_Vw
https://developer.mozilla.org/en-US/docs/Web/Security/HTTP_strict_transport_security
https://www.eff.org/deeplinks/2014/02/websites-hsts

# BONUS: More Security Tips for Node.js



## JSON Web Token (JWT)

So what about combatting CSRF? I've got one bizarre word for you: "jots" --which is how you pronounce JWTs --which is short for JSON Web Tokens --which is short for JavaScript Object Nota...

JWTs make CSRF impossible

## Lusca for Express.js
