---
layout: default
title: Development and Debugging
category: bp
---

# Development and Debugging

## Introduction

This document details the best practices associated with development and debugging applications.

## Coding
Writing clean and maintainable code should be a priority for every developer. Sloppy programming practices is unprofessional, and shows disdain for your fellow programmers.

- Coding Style guides
	- Spacing and indentation
- logging
- comments
- Directory and file names

## Linting
- JSHint - A popular fork of the original JSLint.
- [ESHint](https://github.com/nzakas/eslint) - A command line JS linter that enables a plugable list of tests. It shows promise as its more flexible than JSHint

See the [Web Coding Checklist](./web_coding_checklist.html) for general guidance on code reviews.


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

## Scaffolding
Scaffolding is a good way to get started with a new development project.
It provides a template and some times prompts the user to be able customized the template.
Some project provides templates for different stages of development from unit testing to mobile development.
When getting started with a new technology or framework is sometimes difficult to users look for a fast way
to get a basic "Hello World" project created.
These scaffolding templates are usually created in the open collaboration by experts on the technology and
try to embed best practices that they them selfs learned over time and want to help others not make again.

Some templates cover basic web apps like putting html, css, and js together to more complex project like
dojo builds with integration into hybrid Apps.

### [Yeoman](http://yeoman.io)


## Code Editing

### Editor Config
### Autocompletation
### Editor Plugins
### Integrated Development Enviroments (IDE)

## [Web Coding Checklist](./web_coding_checklist.html)
]


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->


