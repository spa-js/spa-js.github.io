---
layout: default
title: Performance - Images
category: bp
---

# Performance - Images

- Use image sprites and CSS image offfsets
- Use CSS media queries to only load the proper size image for device
- Provide proper images sizes for target devices. Scaling images is expensive, especially for mobile devices.
- Consider data-uri in CSS over discreet files for small images like icons.
- Consider inline SVG images in HTML, or convert SVG to data-uri and put into CSS
- Font icons can be used instead of small image files and defined using `@font-face` rule in CSS.
	- [Font Awesome](http://fortawesome.github.io/Font-Awesome/) has a great collection of icons defined this way.
- Reduce image sizes
	- Save as best file type for the image. (ie. JPEG for photos, PNG for graphics/screen shots, WebP for anything)
	- Reduce quality where practical. 75% quality is not useually noticeable, but make large file size reduction.
	- Ref: [HTML5 Image Compression Article](http://www.html5rocks.com/en/tutorials/speed/img-compression/)



## References


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

