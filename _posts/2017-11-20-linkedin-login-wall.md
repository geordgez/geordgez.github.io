---
layout: post
title: "LinkedIn Login Wall"
date: 2017-11-20
---
This is a quick fix for people who don't have a LinkedIn account or otherwise
don't want to log in and let others know when they've viewed a profile.

If you've hit the hard login wall where the profile preview doesn't load, just
clear your cookies, cache, etc.
[CCleaner](https://www.piriform.com/ccleaner/download) is useful for clearing
across all browsers.

## Steps
1. Right click the transparent dark area around the login prompt
2. Inspect Element
3. Delete the `div` element that's highlighted to remove the overlay
    - The element should be similar to:
      ```
      <div class="show-login no-animation show" id="advocate-modal">
      ```
4. Search for the `overflow` attribute of the `body.advocate-modal-visible` in
the CSS and delete the line `overflow: hidden` to remove the scroll lock
    - Navigate to the body level e.g. `html.os-mac > body#...`.
    - Modify the following CSS:
      ```
      body.advocate-modal-visible {
        overflow: hidden;
      }
      ```
