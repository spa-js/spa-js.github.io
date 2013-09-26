---
layout: default
title: Performance - Mobile
category: bp
---

# Performance - Mobile

- Keep the DOM small. Instead of hiding `<divs>`, move them into a "domCache" (documentFragment). Then when needed again, move it back into the main DOM.
- Minimize the use of Social media buttons, which can add up to a full second in load time PER button
- Android hybrid concerns
	- Move `<uses-sdk>` element to the top of AndroidManifest.xml. (Need reason/ref)
	- Set `android:anyDensity` to true. (Need reason/ref)


## References


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

