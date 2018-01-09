---
layout: post
title: "XSS, CSP, and a Farewell to Bookmarklets"
date: 2017-12-31
---
## XSS, CSP, and a Farewell to Bookmarklets

When [automating the removal of the LinkedIn login wall](https://geordgez.github.io/jots/2017/12/18/linkedin-login-skipping-methods), I tried out a few methods for quickly modifying HTML/CSS.

I was eventually inspired by the
[NYClean bookmarklet](http://euri.ca/2011/get-around-new-york-times-20-article-limit/index.html)
that removed a similar paywall for The New York Times. Just like LinkedIn, The New York Times would block your browsing if you exceeded their article limit by hitting you with some HTML/CSS elements. Since the full content of the original article was still being delivered with the added visual impediments, however, you could read the article free of obstructions if you just manually edited the HTML/CSS in the browser's element inspector/console. *Note: The New York Times has changed their paywall approach since then, thus rendering NYClean obsolete.*

Here's a headline from 2011 on the NYClean bookmarklet:
[That was quick: Four lines of code is all it takes for The New York Times’ paywall to come tumbling down](http://www.niemanlab.org/2011/03/that-was-quick-four-lines-of-code-is-all-it-takes-for-the-new-york-times-paywall-to-come-tumbling-down-2/).

There's actually a wide variety of bookmarklets that serve as lightweight browser add-ons; NYClean demonstrates their potential simplicity and utility. Unlike add-ons, bookmarklets also have the added benefit that they just live in your bookmarks folder/menu/toolbar and don't need to be installed; you can just click them when you need them.

Unfortunately, bookmarklets aren't very practical now because of the [Content Security Policy (CSP)](https://www.owasp.org/index.php/Content_Security_Policy_Cheat_Sheet). It's a standard security feature implemented relatively recently that prevents cross-scripting (XSS), clickjacking, data/content injection, etc. Although not a hard requirement, modern sites are generally encouraged to use CSP headers since they prevent a wide range of web security issues.

CSP means much safer browsing but it also kills the reliability of bookmarklets. Many sites nowadays will prevent a client-side bookmark from executing scripts.

You can test this yourself by creating a simple, innocuous bookmarklet:
```
javascript:alert('hello')
```

Some sites where you'll get an alert when you click on your bookmarklet:
[Google](https://www.google.com/), [Yahoo](https://www.yahoo.com/).

Some sites where nothing happens:
[Instapaper](https://www.instapaper.com/), [GitHub](https://github.com/).

In fact, for the sites where nothing happens, you can inspect your console to see the message that the bookmarklet script is blocked. GitHub, for instance, displays the following message when the bookmarklet is clicked:
```
Content Security Policy: The page’s settings blocked the loading of a resource at self (“script-src https://assets-cdn.github.com”).
```

Even for sites where the bookmarklet may not work, however, you can always execute the desired JavaScript in the console. If you run:
```
alert('hello!')
```
in your browser's console you'll still get the alert to pop up. CSP just prevents you from running the script with a browser bookmark.

### Further tangential reading

A popular bookmarklet was/is [Instapaper's **save** link](https://www.instapaper.com/save) for stashing online articles (similar to Pocket).

Brian Donahue of Instapaper [has a great summary on the death of the bookmarklet](https://medium.com/making-instapaper/bookmarklets-are-dead-d470d4bbb626).

[Here's an article](https://www.linkedin.com/pulse/content-security-policy-michal-koczwara) with examples of sites not implementing CSP.

[Lifehacker](https://lifehacker.com/395697/top-10-useful-bookmarklets) and [Hongkiat Lim](https://www.hongkiat.com/blog/100-useful-bookmarklets-for-better-productivity-ultimate-list/) provide some bookmarklets that were popular (and useful) back in the day.
