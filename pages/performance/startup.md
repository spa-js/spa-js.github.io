---
layout: default
title: Performance - Startup
category: bp
---

# Performance - Startup

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

