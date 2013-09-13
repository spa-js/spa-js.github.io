# Application Architecture

## Introduction

This document details the best practices when designing modern desktop and mobile single page apps (SPAs).

## Layered Approach
There are several different layers of functionality that impact SPAs, as shown in the following figure.
You may be asking yourself what's a **Bijit**? It stands for "Business Widget", and for now, just accept that it is a self-contained unit of work.

![SPA layered environment](./images/app-layers.png)

Let's pick each layer apart from the bottom up, and describe why each is vital to a well designed application.

### Browser Runtime
HTML5 was supposed to be the great unifier. Someday, we may actually get there, but today there is a still a very real issue with different browsers support of the standards. Developers will always want to use the latest and greatest solutions available. But, if you don't control the targeted runtime, which is the norm, then its best to base to the lowest common denominator. This has always been Internet Explorer. Microsoft has done a great job recently of both trying to kill off the oldest and worst of its browsers, as well as ensuring its latest offerings on on near par with the rest of the "modern browsers".

#### Dedicated Development Browser
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

#### Testing With Different Browsers
It should go without saying that you should test your app on as many different browsers -- and on different operating systems -- as practical. While coding for standards will normally keep you in the clear on most browsers, there are always the exceptions and non-support of some standards. Older Internet Explorer browsers are a focal point on this issue.

For Hybrid applications, Chrome (WebKit) has historically been the best browser to test with during development, as most mobile platforms utilize WebKit rendering. This and Chrome's excellent developer tooling. Now that Google Chrome is moving off WebKit onto "Blink", things are less obvious. We'll have to wait and see how well the compatibility is between WebKit and Blink.


### Base Toolkit(s)
The best advice that can be given is "Why reinvent the wheel, when so many others have already done it for you."

#### Dojo
#### JQuery

### Application Foundation

### App Views

### App Bijits
A Business Widget (bijit) is a self contained unit of work. You can think of it as a specialized black box, that can act as its own mini-application. It has no knowledge of its external environment, having a fixed set of inputs, and publishes state changes for any consumer.

A bijit is a conceptual encapsulation of a fixed set of assets. Typically, a bijit consists of a JavaScript controller and an HTML template. It may optionally support a custom Style sheet and runtime configuration.





## API Design
	- Secrets of Awesome JavaScript API Design - Web Standards Sherpa

## Backend Services
	- Urban Airship - Powering Push Notifications, In-App Purchase, and Subscriptions for mobile applicati…

- Browser-specific Guidance
	- CSS3 3D Transforms in IE10 - IEBlog - Site Home - MSDN Blogs

- Device Browser Shell Integration
	- How node.js is integrated with chromium · rogerwang-node-webkit Wiki
	- Mozilla Labs » Blog Archive » Prism is now Chromeless
	- rogerwang-node-webkit

- Feature Detection
	- JavaScript Feature Detection with has.js
	- Modernizr- the feature detection library for HTML5-CSS3
	- The All-In-One Almost-Alphabetical Guide to Detecting Everything - Dive Into HTML5

- Media Queries and Responsive UI Libraries
	- adamdbradley-foresight.js
	- Grid systems
	- Grid systems/Generate a CSS Grid with Stylus
	- Grid systems/stinoga-columnus
	- Responsive CSS Layouts
	- Responsive CSS Layouts/Getting started · Bootstrap
	- scottjehl-Respond
	- WebKit Has Implemented srcset, And It's A Good Thing | Smashing Mobile

- Modular Systems
	- AMD · amdjs-amdjs-api Wiki
	- Module Loaders
	- Module Loaders/timjansen-sparkplug.js · GitHub

- MVC - MV"Whatever" Architectures
	- Speaker Deck - Share Presentations without the Mess

- Web Graphics
	- Sprites
		- Making Sprite-based Games with Canvas


## Data Management
Data drives almost all apps. Balancing access to current data, versus performance is critical to a successful user experience. Sometimes we don't have a choice.

- Data contracts
- Course vs fine grained data access
- Service calls fail, deal with it! (or dont)
- Get only what you need
- Formats XML v JSON
- Transcoding
- Storage issues (caching, session, encryption, size, etc)


## Globalization
- NEVER hard code strings
- The browser defines the language and locale
-

## Responsive Design
- Describe whay and why not to use RD
- Mobile browsers have two size (landscape and portrait)
- Let toolkits do the heavy layout lifting for you.
- Media Queries
- Div relocation

## Images
- Size for target platform, or use SVG.  What browsers?  Still an issue?
- Sprites
- Drive through CSS where practical.


##Accessibility
- Take [Google's Introduction to Web Accessibility](https://webaccessibility.withgoogle.com/course) course
- [Validate](http://validator.w3.org/) your page to ensure its well formed.
- Use A11Y tools to ensure compliance.
	- Screen readers: ChromeVox, (list others)
	- Rational XXX tools
- Use HTML5 semantic nodes like `<nav>` and `<header>`
- Use proper input tags (eg `<button>` and `<a>`) for nodes with event handlers like `onClick`.
- Use linked `<label` tags for all input elements.
- Use CSS for layout, not tables.


## Application Project Structure

<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->


