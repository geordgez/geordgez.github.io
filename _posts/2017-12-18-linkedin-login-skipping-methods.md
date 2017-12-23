---
layout: post
title: "Automatically and/or Quickly Skipping the LinkedIn Login Wall"
date: 2017-12-18
---

*This is a follow-up to
[another post](https://geordgez.github.io/jots/2017/11/20/linkedin-login-wall)
about manually skipping the LinkedIn login wall.*

## Automatic goggles
As noted before, every LinkedIn profile has a public version that can be viewed
without logging in. The only time you might not be able to view it is if you
have viewed more than one profile/day without logging in. When this happens, the
page still loads the complete public profile but makes it difficult to be
viewed in the browser by imposing a paywall and scroll lock. However, since
this is just the result of superimposed elements and CSS, you can view the
profile as if it were your first profile of the day i.e. an obscured view of
the public profile free of any login wall shenanigans.

After manually editing CSS elements one too many times on LinkedIn, I realized
that there must be a simple, automatic way to override the login wall each
time I browsed LinkedIn.

Here I note and provide a few ways of doing this:
1. A Bookmarklet!
1. JavaScript that can be copied and pasted into the console
2. uBlock Origin custom filtering rules
3. A browser add-on to apply user-specified stylesheets (not recommended)
4. Browser-specific methods of enforcing custom user stylesheets

If you find any issues or bugs, feel free to submit an issue in
[my repo for this project](https://github.com/geordgez/linkedin-login-wall-css).

### Simple, non-invasive fix: Bookmarklet
[bookmarklet]: javascript:(function() {document.getElementById('advocate-modal').style.display = "none";document.getElementById('pagekey-public_profile_v3_desktop').style.overflow = "visible";document.getElementsByClassName('js%20guest%20advocate-modal-visible')[0].style.overflow = "visible";})();  "Bookmarklet"

Trying this out [Bookmarklet][]

Or create a bookmark and copy and paste this as the location:
```
javascript:(
  function() {
    document.getElementById('advocate-modal').style.display = "none";
    document.getElementById('pagekey-public_profile_v3_desktop').style.overflow = "visible";
    document.getElementsByClassName('js%20guest%20advocate-modal-visible')[0].style.overflow = "visible";
  }
)();
```

### Quick temporary fix: JavaScript in the Console
If you don't want to install anything, here's some really simple JavaScript
that you can paste into your browser console each time:

```
document.getElementById('advocate-modal').style.display = "none";
document.getElementById('pagekey-public_profile_v3_desktop').style.overflow = "visible";
document.getElementsByClassName('js guest advocate-modal-visible')[0].style.overflow = "visible";
```

To get to the browser console, find a blank spot on a web page in your
browser window, right-click, and select `Inspect`, `Inspect Element`, or
your browser's equivalent in the resulting dropdown menu.

### Single, permanent fix: uBlock Origin
Add the following lines in uBlock Origin Settings > My Filters:

```
linkedin.*###advocate-modal

linkedin.*##body.advocate-modal-visible:style(overflow:visible;)
```

Honestly, you should have uBlock Origin on your computer regardless of whether
you care about this fix to automatically remove the LinkedIn login wall.

### Single, permanent, but insecure and suboptimal fix: Stylish
**Caveat for privacy-minded folks:** Please be aware that Stylish
[recently adopted an opt-out data collection policy](https://forum.userstyles.org/discussion/53233/announcement-to-the-community).
Based on the
[privacy policy (as of October 30th, 2017)](https://userstyles.org/login/policy),
it appears that you can only [opt out via email](mailto:contact@userstyles.org).

[Stylish](https://userstyles.org/) is a popular browser add-on
for applying custom user stylesheets:
- [Chrome version](https://chrome.google.com/webstore/detail/stylish-custom-themes-for/fjnbnpbmkenffdnngjfgmeleoegfcffe?hl=en)
- [Firefox version](https://addons.mozilla.org/en-US/firefox/addon/stylish/)

I added
[a small CSS stylesheet](https://userstyles.org/styles/153015/remove-linkedin-login-wall)
that can be added via the Stylish add-on to remove the soft login wall that
was noted in the previous post.

### Similar and superior options to Stylish
Some other add-ons exist for this purpose (such as
[User CSS](https://chrome.google.com/webstore/detail/user-css/okpjlejfhacmgjkmknjhadmkdbcldfcb?hl=en),
[Stylebot](https://chrome.google.com/webstore/detail/stylebot/oiaejidbmkiecgbjeifoejpgmdaleoha?hl=en), and
[Stylish](https://chrome.google.com/webstore/detail/stylish-custom-themes-for/fjnbnpbmkenffdnngjfgmeleoegfcffe?hl=en)
for Chrome
)
but I ended up creating a Stylish sheet since it seemed to be the most popular.

### Native in-browser options
Firefox natively [supports custom CSS](https://superuser.com/questions/318912/how-to-override-the-css-of-a-site-in-firefox-with-usercontent-css).
Chrome apparently
[stopped supporting this feature in 2014](https://www.itsupportguides.com/knowledge-base/computer-accessibility/how-to-use-a-custom-style-sheet-css-with-google-chrome/).
