---
layout: default
title: Testing
category: bp, app-arch
---


# Testing

## Introduction

## Unit tests

## Test Driven Development

## Debugging
- Your browser: know your main test tool!

### Dedicated Development Browser
Use a dedicated "development" browser, that is different than your day-to-day browser. I use Chrome for my normal browser, and Chrome Canary as my development browser. This keep a clean separation of concerns between the environments. My dev browser has its own set of bookmarks specific to the projects I am working on. It also has custom startup options to disable Application Cache and Cross-Domain Security. Finally, It also has a full compliment of development specific plugins. While your choice of preferred plugins is likely different, these are the ones that I have installed.
- Accessibility Developer Tools - For analyzing A11Y compliance
- ADB - Android remote debugging
- ChromeVox - Screen reader for A11Y compliance
- ColorPick Eyedropper - Identifying color values
- Edit This Cookie - Cookie management
- IBM Rational Functional Tester - Comprehensive testing web apps
- JSONView - For structured viewing of JSON data
- PageSpeed Insights - Performance analysis
- Postman - REST client
- Ripple Emulator - BlackBerry testing
- Web Developer - General set of testing tools
- Web Performance - Performance analysis
- XHR Poster - REST client
- YSlow - Performance analysis



### Testing With Different Browsers
It should go without saying that you should test your app on as many different browsers -- and on different operating systems -- as practical. While coding for standards will normally keep you in the clear on most browsers, there are always the exceptions and non-support of some standards. Older Internet Explorer browsers are a focal point on this issue.

For Hybrid applications, Chrome (WebKit) has historically been the best browser to test with during development, as most mobile platforms utilize WebKit rendering. This and Chrome's excellent developer tooling. Now that Google Chrome is moving off WebKit onto "Blink", things are less obvious. We'll have to wait and see how well the compatibility is between WebKit and Blink.

### Internet Explorer

Internet Explorer (IE) has been the bane of web developers since the beginning. It has historically been very non-compliant in regards to Web standards, and is always a source of web app bugs. Also, it has also had terrible debugging capabilities. For this reason, developers typically shun testing in IE until the very end of development, even knowing new bugs will be reported on this platform. I wont even talk about about its horrible performance.

Starting with IE10, things are much better. We are seeing strong standards support -- although there is are still large gaps -- and we now have a real debugger to aid in tracking down those bugs unique to IE. Its still safe to say that IE will likely still be the source of platform specific bugs

For these reasons, test with Internet Explorer continuously during development. Do not save it for last. Otherwise, this **will** cause release delays when those IE specific bugs are discovered during final testing. Remember, IE is still, and likely will remain the most popular desktop browser, so you must support it, and its older, headache inducing versions.



