---
layout: default
title: Shims and Polyfills
category: bp, app-arch
---

# Shims and Polyfills


![SPA layered environment](./images/app-arch-layers.png)



Those that take developing modern web apps seriously watch the new emerging technologies with a bit of melancolie. On one hand you have these really cool and exciting new technologies. But, on the other hand, you know it will 5-10 years before the majority of your user's browsers will be expected to support them. Things are beginning to look up though. Browsers are updated much more frequently than in the past, with forced upgrades. Also, many JavaScript toolkits provide shims to provide a facade for differences in API's and implementation to ensure consistent browser behavior.

Polyfills are a way to enable discreet JavaScript to enhance browsers that lake native functionality of the newest features and standards. Google's [Polymer](http://www.polymer-project.org/) is a new platform that aims to bring tomorrow's standards onto current platforms. If a given feature is not natively available on the user's browser Polymer will fills the gap through provided its provided library. While there may be a slight performance hit when non-native, the end goal is there for you to exploit. The ground covered by Polymer is extensive and too involved to describe in this document. But you are encouraged to get into Polymer and see what it has to offer your apps.

Using Polymer, and possibly other shim and polyfill libraries, you can develop cool apps using the latest emerging technologies. Never force users to deal with Web apps that look and feel like they were developed in the previous decade. The future is now (well, at least very soon!). Exploit it.

