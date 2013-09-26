---
layout: default
title: Performance - CSS
category: bp
---

# Performance - CSS

- Optimize CSS to inline `@include` external CSS files
- Use CSS3 instead of images. Things like gradients, shadows, and rounded corners are faster through CSS than using discreet images.
- Use CSS3 advance styling in moderation
	- Rules such as box-shadow are expensive to process
- Remove unused CSS rules. This just adds code bloat, complicates rendering, and app maintenance.
	- Ref: [Google's Make the Web Faster](https://developers.google.com/speed/docs/best-practices/payload#RemoveUnusedCSS)
	- Keep selectors simple. CSS parsers work from right to left, which is counter-intuitive. You want selectors to go from course to fine, not fine to course grained.
			- Ref: [Google Optimize browser rendering](https://developers.google.com/speed/docs/best-practices/rendering#UseEfficientCSSSelectors)
			- (Need Examples)
- [CSS Optimizations for Compositing Hardware](http://ariya.ofilabs.com/2013/06/optimizing-css3-for-gpu-compositing.html)
- Avoid dynamic CSS language compilation at runtime
	- When using 'less' or other CSS compilers, they should be run at build/deploy time, not at runtime.
	- Anti-pattern shown below. The following lines force the styles.less to be transformed into a .css file at runtime. This should be done in a build step, so that only the styles.css is included.

```
    <link href="css/styles.less" rel="stylesheet/less" type="text/css">
    <script src="./js/less.js"></script>
```


## References


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

