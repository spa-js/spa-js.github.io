---
layout: default
title: Performance - Mobile
category: bp
---

# Performance - Mobile

- Use touch events, not click events
	- mobile browsers by default will add an artifical delay to click event to see if they are actually double-clicks, or drag events.
	- Most mobile toolkits handle this for you, but double check.

- Disable slow transition effects for older devices
	- Slides and fades are very janky on old devices.
	- Use feature detection to determine the device your on, and if its an old O/S (ie Android 3.2 or below), just disable all transitions

- Keep the DOM small. Instead of hiding `<divs>`, move them into a "domCache" (documentFragment). Then when needed again, move it back into the main DOM.

- Minimize the use of Social media buttons, which can add up to a full second in load time PER button

- Use activity indicators (spinners) sparingly.
	- Often times it just brings attention to the user how long he is waiting for an action to complete
	- Other animations can distract the user without feeling like he's waiting

- Android hybrid concerns
	- Move `<uses-sdk>` element to the top of AndroidManifest.xml. (Need reason/ref)
	- Set `android:anyDensity` to true. (Need reason/ref)

## References
- [A Beginner's Guide to Perceived Performance: 4 Ways to Make Your Mobile Site Feel Like a Native App](http://www.mobify.com/blog/beginners-guide-to-perceived-performance/)

<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

