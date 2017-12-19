---
layout: post
title: "Automatically Skipping the LinkedIn Login Wall"
date: 2017-12-16
---

*This is a follow-up to
[another post](https://geordgez.github.io/jots/2017/11/20/linkedin-login-wall)
about manually skipping the LinkedIn login wall.*

## Automatic goggles
After manually editing CSS elements one too many times on LinkedIn, I realized
that I should probably just find a simple, automatic way to override the CSS
each time I was browsing LinkedIn.

Here I note and provide two ways of doing this:
1. A draggable button/link
2. A browser add-on to apply user-specified stylesheets

If you find any issues or bugs, feel free to submit an issue in
[my repo for this project](https://github.com/geordgez/linkedin-login-wall-css).

# Quick fix

### Draggable button/link
TODO

### Inspiration
There's been some discussion regarding soft paywalls/login walls; I learned
about a particular example with the New York Times online article access;
see the news article on that issue
[here](http://www.niemanlab.org/2011/03/that-was-quick-four-lines-of-code-is-all-it-takes-for-the-new-york-times-paywall-to-come-tumbling-down-2/)). The basic idea was that the
New York Times website would display a paywall that would ask you to
pay for a subscription in order to continue reading after you hit a certain
number of articles. Whether intentionally or accidentally, the paywall was
"soft" in that even though the page would darken and display a notification
blocking your view of the article contents, the actual contents would
completely load in your browser.

If you're an odd mix of lazy (like me) and
persistent and also know a just enough about the web, you could right click
the page and view source to get the article. The actual article would be ugly,
but you'd be able to read it!

This is actually the same thing that LinkedIn does; even though you may get
hit with this soft login wall that apparently blocks your view after looking
at more than one profile, your browser still gets all the contents of the
profile that the user has allowed public viewership of. You could manually
remove the CSS elements each time this happens but that gets annoying after a
while.

Of course, sometimes LinkedIn might actually serve you a hard login wall
that doesn't actually load any profile contents; all your browser gets is the
login wall that you're redirected to. In that case, clearing your cookies and
cache usually helps (see the
[previous post](https://geordgez.github.io/jots/2017/11/20/linkedin-login-wall))
but this is also a tedious process.

Additionally, you can always switch IP addresses, e.g. use VPN or a different
device to browse LinkedIn profiles, but at that point you've probably wasted
more time and effort than if you had just logged in (unless you really, really
want to hide the fact that you viewed someone's profile).

The news article also talks about the
[simple widget](http://euri.ca/2011/get-around-new-york-times-20-article-limit/)
that David Hayes built in 2011 for reading the New York Times online; you could
drag it to your browser toolbar and click whenever you hit the soft paywall.
I thought that his tool was pretty nifty and pain-free to use so I decided to
make one like it.


# Forcing custom CSS via add-on

### Stylish
[Stylish](https://userstyles.org/) is a popular browser add-on
for applying custom user stylesheets:
- [Chrome version](https://chrome.google.com/webstore/detail/stylish-custom-themes-for/fjnbnpbmkenffdnngjfgmeleoegfcffe?hl=en)
- [Firefox version](https://addons.mozilla.org/en-US/firefox/addon/stylish/)

I added
[a small CSS stylesheet](https://userstyles.org/styles/153015/remove-linkedin-login-wall)
that can be added via the Stylish add-on to remove the soft login wall that
was noted in the previous post.

**Caveat for privacy-minded folks:** Please be aware that Stylish
[recently adopted an opt-out data collection policy](https://forum.userstyles.org/discussion/53233/announcement-to-the-community).
Based on the
[privacy policy (as of October 30th, 2017)](https://userstyles.org/login/policy),
it appears that you can only [opt out via email](mailto:contact@userstyles.org).


### Some other options
Some other add-ons exist for this purpose (such as
[User CSS](https://chrome.google.com/webstore/detail/user-css/okpjlejfhacmgjkmknjhadmkdbcldfcb?hl=en),
[Stylebot](https://chrome.google.com/webstore/detail/stylebot/oiaejidbmkiecgbjeifoejpgmdaleoha?hl=en), and
[Stylish](https://chrome.google.com/webstore/detail/stylish-custom-themes-for/fjnbnpbmkenffdnngjfgmeleoegfcffe?hl=en)
for Chrome
)
but I ended up choosing Stylish since it seemed to be the most popular.

### Native in-browser options
Firefox natively [supports custom CSS](https://superuser.com/questions/318912/how-to-override-the-css-of-a-site-in-firefox-with-usercontent-css).
Chrome apparently
[stopped supporting this feature in 2014](https://www.itsupportguides.com/knowledge-base/computer-accessibility/how-to-use-a-custom-style-sheet-css-with-google-chrome/).
