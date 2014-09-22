---
layout: post
title: "Web Security Fundamentals - Part 2: More Info on Defense"
date: 2014-09-22 8:26
comments: true
categories:
  - web tech
  - security
  - technical posts
  - JavaScript
  - Node.js
  - Express
---

Last Thursday, I published [a blog post](/blog/2014/09/18/web-security-fundamentals-by-google-peeps/) in which I summarized the main attack techniques (XSS, CSRF, and MITM) used by baddies to screw with the web. That post also covered two header-based solutions available to help you defend your site: CSP and HSTS. To supplement all that info, I am providing a bunch of articles, references, videos, and tools to help you learn more and take advantage of CSP and HSTS.

# Content Security Policy (CSP)

### Browser Support

Cross-browser support for CSP is [pretty good](http://caniuse.com/#feat=contentsecuritypolicy). The latest versions of IE require the CSP header to use a special prefix (much like vendor prefixes for certain CSS features). Older crap like IE9 and below have no CSP support.

### Further Reading/References

- [HTML5 Rocks - Intro to CSP](http://www.html5rocks.com/en/tutorials/security/content-security-policy/)
- [MDN - CSP Topics](https://developer.mozilla.org/en-US/docs/Web/Security/CSP)
- [CSP Cheatsheet](http://content-security-policy.com/)
- [Yelp Engineering Blog - CSP at Scale](http://engineeringblog.yelp.com/2014/09/csp_reports_at_scale.html)

#### Awesome Presentation on CSP
<iframe width="300" height="169" src="//www.youtube-nocookie.com/embed/pocsv39pNXA" frameborder="0" allowfullscreen></iframe>

# HTTP Strict Transport Security (HSTS)

### Browser Support

Most browsers get a passing grade when it comes to HSTS support --except for...

{% blockquote Electronic Frontier Foundation (EFF), https://www.eff.org/deeplinks/2014/02/websites-hsts Websites Must Use HSTS in Order to Be Secure %}
Internet Explorer doesn't support HSTS—which means that there's basically no such thing as a secure website in IE
{% endblockquote %}

### Further Reading/References

- [MDN - HSTS Overview](https://developer.mozilla.org/en-US/docs/Web/Security/HTTP_strict_transport_security)
- [EFF - HSTS is a must](https://www.eff.org/deeplinks/2014/02/websites-hsts)
- [Leviathan - Caveat for using HSTS with wildcard SSL certificates](https://www.leviathansecurity.com/blog/the-double-edged-sword-of-hsts-persistence-and-privacy/)

#### Quick Video Summary of MITM and HSTS

<iframe width="300" height="169" src="//www.youtube-nocookie.com/embed/zEV3HOuM_Vw" frameborder="0" allowfullscreen></iframe>

**Note:** The video above provides *outdated* browser support info. Updated info can be found here: [CanIUse.com](http://caniuse.com/#feat=stricttransportsecurity).

# Bonus: Security Toolkit for Express Apps

## Lusca

Do you use Node.js? Does your Node.js app use Express? Want some middleware to help secure that app? Perhaps you should consider using [Lusca](https://github.com/krakenjs/lusca), a free module created by Paypal to quickly add and configure various security features such as CSP and HSTS. I haven't personally tried it yet, but I plan to do so soon. Their README file makes Lusca look very easy for devs to use.

You can pick and choose which security features you want to enable. For example, if you're already using [JSON Web Tokens](http://angular-tips.com/blog/2014/05/json-web-tokens-introduction/), then you may not want to use Lusca's CSRF method while you take advantage of Lusca's legacy browser XSS protection.

By the way, don't get confused: Paypal uses their own open-source, Express-based framework called KrakenJS, but Lusca works with Kraken apps *and* Express apps.

#### Presentation on Securing SPAs and Node.js Apps (by PayPal Engineer)

<iframe width="300" height="169" src="//www.youtube-nocookie.com/embed/40-Ccq6b5lk" frameborder="0" allowfullscreen></iframe>
