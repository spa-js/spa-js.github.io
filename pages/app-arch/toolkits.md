---
layout: default
title: Toolkits
category: bp, app-arch
---

# Toolkits, Shims and Polyfills, and Libraries

![SPA layered environment](./images/app-arch-toolkits.png)

## Introduction

We are lumping several topics into this area as the lines blur quickly when discussing this layer of the architecture. Effectively, any web app will utilize a base JavaScript toolkit from which to build on top of. Then, you may opt to utilize Shims and Polyfills to provide advanced technologies that are not consistently standardized on within browsers. Finally, one or more extra specialized libraries may be used to add additional feature above what is provided in the base toolkit.


## Base Toolkit(s)

The best advice that can be given is "Why reinvent the wheel, when so many others have already done it for you."  There is a wealth of JavaScript toolkits that can have an enormous impact on the quality of your app. In fact it is unheard of to attempt any medium to large scale Web app without utilizing a base toolkit. The base toolkit provides a generalized JavaScript environment and consistent API. Typically, your company will standardize on a single base toolkit to use in Web apps. As standards advance, a lot of functionality of toolkits should diminish. We still feel there will always be a place for quality toolkits to reduce boilerplate code and general application scaffolding.

In the following section, we'll list general areas, and what we think are the top toolkit providers. We wont recommend specific toolkits, as we'll that to you to find solutions that work for you and your projects requirements.

### [JQuery](http://jquery.com/)
JQuery is by far the most popular general purpose toolkit for web sites. At its core is a fast DOM query mechanism to access and manipulate elements. It also provides a consistent AJAX API, simple effects, and event handling. There are several extensions to JQuery that provide extra features, such as:

- [JQuery UI](http://jqueryui.com/)
- [JQuery Mobile](http://jquerymobile.com/)
- [Several hundred](http://plugins.jquery.com/) community sourced plug-ins

Jquery's strengths are its ubiquity, ase of learning, documentation, and strong community. It comes up short on large projects, as scalability and maintenance can be an issue. Other areas of concern include potential copyright, licensing, and API inconsistency across its plugins.

### [Dojot Toolkit](http://www.dojotoolkit.org)
Dojo takes a radically different approach to being a toolkit. It makes everything available at once in its base package. There are hundreds of modules that span everything from basic APIs, widgets, mobile, animations, charting, graphing, and much more. The Dojo foundation manages all the components, so there is consistent quality, API signature, and licensing. The down side is that Dojo incurs a comparatively steep learning curve compared to JQ.

### [AngularJS](http://www.angularjs.org/)
This is a relative new comer to the toolkit scene. Developed by Google, Angular is gaining a rapid fan base for being a solid application platform.
- [Video: AngularJS Fundamentals In 60-ish Minutes](https://www.youtube.com/watch?v=i9MHigUZKEM) - Great introductory video on using Angular.

### [SemanticJS](http://semantic-ui.com/)
Another new toolkit that contains a nice and clean implementation for layouts and common widget.

### [Underscore]() / [Lowdash]()
Both of these toolkits provide a simple layer that provides a consistent basic JS API across all browsers. These are bare bones, no frills toolkits, but are very effective and fast. These should be considered as a minimum solution to any web app.  They are also frequently dependents for many other libraries.

### Others
The list of other options is far to long to provide here, but a couple popular and established toolkits include:

- [ExtJS](http://www.sencha.com/products/extjs/) - Sencha's entry.
- [YUI]() - Yahoo's toolkit that comes with a very nice set of widgets
- [MooTools]()


## Shims and Polyfills

Those that take developing modern web apps seriously watch the new emerging technologies with a bit of melancholia. On one hand you have these really cool and exciting new technologies. But, on the other hand, you know it will 5-10 years before the majority of your user's browsers will be expected to support them. Things are beginning to look up though. Browsers are updated much more frequently than in the past, with forced upgrades. Also, many JavaScript toolkits provide shims to provide a facade for differences in API's and implementation to ensure consistent browser behavior.

Polyfills are a way to enable discreet JavaScript to enhance browsers that lake native functionality of the newest features and standards. Google's [Polymer](http://www.polymer-project.org/) is a new platform that aims to bring tomorrow's standards onto current platforms. If a given feature is not natively available on the user's browser Polymer will fills the gap through provided its provided library. While there may be a slight performance hit when non-native, the end goal is there for you to exploit. The ground covered by Polymer is extensive and too involved to describe in this document. But you are encouraged to get into Polymer and see what it has to offer your apps.

Using Polymer, and possibly other shim and polyfill libraries, you can develop cool apps using the latest emerging technologies. Never force users to deal with Web apps that look and feel like they were developed in the previous decade. The future is now (well, at least very soon!). Exploit it.


## General Purpose Toolkits
Other more specialized toolkits focus on specific requirements of an app.
The following toolkits are focused on providing a robust platform for developing web applications.

### MVC
- [Backbone.js](http://backbonejs.org/)
- [Ember](http://emberjs.com/)
- [AngularJS](http://angularjs.org/)
- [KnockoutJS](http://knockoutjs.com/)

