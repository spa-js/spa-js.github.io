# Performance

## Introduction

This document describes a collection of generally accepted best practices regarding Web app performance.

## Startup concerns
First impressions are critical for any Web App.  This is even more obvious for attention distracted mobile users. Your app must load fast enough to keep the user from doing something else, or simply abandoning the app altogether. There are many approaches to improve app startup as shown below.

- Load only enough to put something interesting on the glass.
	- Create a simple bootstrap module that can get the user to the initial home or login screen. Do not bundle everything into a master layer here.  You want the bare minimum here.
	- The initial Dom body should be as minimal as possible.  Do not include the entire site's collection of potential views by default.  We can inject them later.
	- Extended splash or loading screens should be avoided if possible. These are annoying and actually increase the perceived loading time.
- Load anything else needed immediately in the background.
	- Users will look at the initial view for at least a couple seconds before taking any action. Use this user based delay to your benefit.
	- Now is the time to load any secondary modules, extra CSS, updated messages, real time data, etc.
- Load everything else either on demand, or pre-fetch on likely user flow.
	- Use analytics to determine typical story flows.
	- On demand loading of views and resources is typically acceptable performance wise. We really don't want to load everything if the user is only going to visit 20% of the entire app's potential.
	- If a user is likely to go form view B to view D, go ahead and preload view D in the background. The user experience will be improved as there is no delay on the new view transition.
- Remove views when no longer needed.
	- This is not really a startup issue, but is related enough to loading to be considered here.
	- this is especially valuable for CPU and memory constrained mobile devices.
	- Keeping the DOM as small is possible greatly improve rendering and reflow operations.
	- Two basic options are to
		- Destroy the view and all its children, saving state if needed. This can actually get quite complex to manage if the child widget and/or state is complex. But, if its unlikely the user will revisit the view again, or there is little stateful concerns, then prune the fat, and clean up memory and DOM resources.
		- Use a DomCache. This involves offloading the view's node tree to a "domCache" (DomFragment) after they have been transitioned out. Then if the view is needed again, reinsert it back into the master DOM. This is good for view likely to be revisited, or requires a lot of state and setup.


## Resource management
The most simple of suggestions is to reduce the number of files loaded by the app.  This needs to be weighed against the need to have a manageable project structure, and overall size.  Yes, we have seen complex web apps that consist of a single humongous file! Its possible to do, but wildly unmaintainable, and incurs a big hit at startup time. Don't do that.

It is important to make it easy during development by having clean separation of concerns, and clean modular sections of the code. The build and deployment process is where you need to focus on optimizing files for performance. File optimization is discussed in detail in the [Continuous Integration document](./continuous-integration.html).  Suffice to say that from a performance perspective file optimization is the single best contributor to a better performing web app.

### JavaScript
- Optimize to combine AMD dependent modules
- Properly optimize all JavaScript and CSS.
	- This is the single best practice for high performing apps, especially when using Dojo.
	- Also ensure that any external libraries are pre-optimized and not in source form.
- Balance Layer sizes and number of files.
	- Use a few base layers that contain frequent and common modules
	- AMD is good at loading multiple modules in parallel.
	- General guidance is layers <500K, and <6 layers/modules loaded at a time.

### CSS
- Optimize CSS to inline `@include` external CSS files
- Use CSS3 instead of images. Things like gradients, shadows, and rounded corners are faster through CSS than using discreet images.
- Use CSS3 advance styling in moderation
	- Rules such as box-shadow are expensive to process
- Remove unused CSS rules. This just adds code bloat, complicates rendering, and app maintenance.
	- Ref: [Google's Make the Web Faster](https://developers.google.com/speed/docs/best-practices/payload#RemoveUnusedCSS)
	- Keep selectors simple. CSS parsers work from right to left, which is counter-intuitive. You want selectors to go from course to fine, not fine to course grained.
			- Ref: [Google Optimize browser rendering](https://developers.google.com/speed/docs/best-practices/rendering#UseEfficientCSSSelectors)
			- [Need Examples]

### Images
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

### Network
- Cache static resources
- Remove unused HTML/JS/CSS/PNG files.
	- This is just bloat and causes longer build times, more difficult maintenance, and larger deployment size.


## Mobile specific concerns
- Keep the DOM small. Instead of hiding `<divs>`, move them into a "domCache" (documentFragment). Then when needed again, move it back into the main DOM.
- Minimize the use of Social media buttons, which can add up to a full second in load time PER button
- Android hybrid concerns
	- Move `<uses-sdk>` element to the top of AndroidManifest.xml. (Need reason/ref)
	- Set `android:anyDensity` to true. (Need reason/ref)

## References
- [Google's Make the Web Faster](https://developers.google.com/speed/?csw=1)
- [Mobile App performancee](http://mobile.smashingmagazine.com/2013/04/03/build-fast-loading-mobile-website/)


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

