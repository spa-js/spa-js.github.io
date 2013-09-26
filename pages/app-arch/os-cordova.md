---
layout: default
title: O/S and Cordova Bridge
category: bp, app-arch
---

# O/S and Cordova Bridge

## Introduction

![SPA layered environment](./images/app-arch-os.png)


## O/S and Cordova Bridge
Typically you will have little to no control the operating system your app is running upon. For desktop apps, this is rarely a concern. But today's "mobile-first" approach to application design and runtime operation, the O/S becomes central to how the app looks and behaves, and interaction with the hardware itself.

Mobile applications frequently mimic the operating system's look and feel. Also known as its theme, it relies on provided style guidelines to achieve a consistent user experience. Other aspects of O/S specific behavior is the existence of a back button, options access, and if the app can be safely placed into the background. Various toolkits, such as Dojox/Mobile, can provide the desired theming, and assist with application navigation and menuing behavior.

Apache's [Cordova](http://cordova.apache.org/) is a runtime library that provides a bridge between the application and various hardware resources like the camera, recorders, or the file system. Cordova is a comprehensive library exposed as Javacript API's, that internally makes HTTP calls to a local service handler that then uses native compiled code to interface directly with the devices hardware. There are several dozen plugins for Cordova that extend the base APIs. Utilizing these plugins extend access to features like Bar Code Scanning, augmented reality, and more. If you should ever find your self in need of native access features not provided by Cordova or one of its plugins, then you can write your plugin, using the O/S's native programming language, Java for Android and Blackberry, or Objective-C for IOS.  These are not just a mobile solution. Using the same topology, Cordova provides opportunities to turn any SPA's into stand-alone applications for desktop O/S's as well.

