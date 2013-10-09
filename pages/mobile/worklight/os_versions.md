---
layout: default
title: Mobile - Worklight - O/S Versions
category: bp
---

# Dealing with New Device O/S Versions

## Introduction

## Examples

- Soft keyboard affects `viewport.height` when shown/hidden dynamically in iOS7, but did not in iOS6.
	- This type of change is done by the browser implementation, and controlled via `<meta>` viewport tag
	- See this [Stackover article](http://stackoverflow.com/questions/18970865/ios-7-input-elements-moving-fixed-positioned-elements)

- It is possible that browser (even native) screen dimensions available to apps might change between major OS versions.
	- The proper way to deal with this is CSS media queries, just as if it's a new type of device with different screen dimensions (even though in this case its caused by the OS/software updates)
	- Specific example is the addl 20px height given to all apps in iOS7 (native/hybrid/web)
	- One possible general solution if you have a header `<div>` in your app is to add `padding-top: 20px` within a media query that matches the iOS7 screen heights (one for portrait and one for landscape) vs. the default that doesn't add the padding
	- Or vice-versa, make the new default styling with the extra padding going forward, and remove the extra top padding in a media query matching the older screen dimensions


- Here's a link to the [iOS7 design guidance](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/TransitionGuide/index.html#//apple_ref/doc/uid/TP40013174-CH6-SW1) that makes it clear that minor changes should be expected as part of this kind of major OS upgrade.  Same can be said for any other mobile vendor platform...plan accordingly during the beta test period to review app for these types of changes.  There is no guarantee that your app will continue to run as it did on previous versions with any architecture type, hybrid, native or web.

