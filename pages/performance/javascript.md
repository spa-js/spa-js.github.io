---
layout: default
title: Performance - JavaScript
category: bp
---

# Performance - JavaScript

- Optimize to combine AMD dependent modules
- Properly optimize all JavaScript and CSS.
	- This is the single best practice for high performing apps, especially when using Dojo.
	- Also ensure that any external libraries are pre-optimized and not in source form.
- Balance Layer sizes and number of files.
	- Use a few base layers that contain frequent and common modules
	- AMD is good at loading multiple modules in parallel.
	- General guidance is layers &lt;500K, and &lt;6 layers/modules loaded at a time.


## References


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

