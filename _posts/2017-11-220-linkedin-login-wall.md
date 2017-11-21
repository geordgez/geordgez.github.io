---
layout: post
title: "LinkedIn Login Wall"
date: 2017-11-20
---
This is a quick fix for people who don't have a LinkedIn account or otherwise
don't want others to know when they've viewed a profile.

## Steps
1. Right click the transparent dark area around the login prompt
2. Inspect Element
3. Delete the `div` element that's highlighted to remove the overlay
4. Search for `overflow` in the CSS and remove the line `overflow: hidden` to remove the scroll lock
