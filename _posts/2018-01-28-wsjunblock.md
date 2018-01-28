---
layout: post
title: "JS-based Login Wall & Paywall Remover"
date: 2018-01-28
---
## JS > CSS
I spent a bit of time building out CSS-based solutions for bypassing the
LinkedIn login wall (see
[post here](https://geordgez.github.io/jots/2017/12/18/linkedin-login-skipping-methods)).
But an extension that also blocks JavaScript-based login walls and paywalls
would cover more bases.

## `wsjUnblock`
Jinsong Li's
[**`wsjUnblock`**](https://github.com/njuljsong/wsjUnblock)
is a good solution; see the
[blog post here](http://blog.jinsongli.com/post/show/31).
As of now, the extension helps with the Wall Street Journal, New York Times,
Bloomberg, and Washington Post. I recently submitted a PR to incorporate
LinkedIn.

I'd recommend using `wsjUnblock` since it's a more holistic framework for
removing obstructions on web pages. I'm planning to dig around LinkedIn to see
if there are any JS-based solutions for handling the hard login wall.

The only downsides to the extension are that:
1. As of January 2018, it only works for Chrome. There is, however,
[an active PR for Firefox and Edge](https://github.com/njuljsong/wsjUnblock/pull/17).
In the meantime, if you use another browser (or you don't want to install an
extension and also don't mind clicking on a bookmark every time to remove the
LinkedIn page obstructions, you can always install my
[*amazing* bookmarklet](https://geordgez.github.io/jots/2017/12/18/linkedin-login-skipping-methods).
But in the end, you should really get `wsjUnblock` instead if you're a heavy
Chrome user.
2. Despite developing wsjUnblock, Jinsong is
[self-listed](https://github.com/njuljsong) as a member of the
"Hearst Digital Media" GitHub group. This isn't a real issue as long as the
extension works, just slightly ironic.

**Thanks, Jinsong!**
