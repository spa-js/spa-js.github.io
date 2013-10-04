---
layout: default
title: Mobile Concerns
category: bp
---



# Mobile Concerns

## Introduction
I know we don't want "Mobile" specific guidance here, but I wanted a place to put notes, tips, etc for now.

## Mobile Apps
- Better to post-fill a view with data after the transition than to build the full view and then transition
Total time is the same, but user perception of “Click > Transition > Fill” is better then “Click > Wait > Transition”

- Dojo Mobile Views - Minimize logic in “onBeforeTransitionOut” and “onBeforeTransitionIn” states.

- Busy indicator can actually lead to worse “perceived” user experience than simply working in silence – for short periods only of course, in the range of a 1-2 seconds maximum.


- [IOS](./ios.html)
- [Android](./android.html)
- [Cordova](./cordova.html)
- [Worklight](./worklight.html)

