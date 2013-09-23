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


## IOS

- Disabled AutoCorrect and AutoCapitalize:
	- ref: [TriceDesigns Mobile/Phonegap tips](http://www.tricedesigns.com/2012/01/17/mobile-web-phonegap-html-dev-tips/)

	<input type="text" autocorrect="off" autocapitalize="on" />


## Android
- Emulation using [Genymotion](http://www.genymotion.com/)



## PhoneGap
- [PhoneGap Command Line](http://log.michaelbrooks.ca/post/phonegap-cli-preview)


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->


