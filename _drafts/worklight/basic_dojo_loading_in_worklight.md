---
layout: post
title:  "Basic Dojo Loading in Worklight apps"
date:   2013-08-05 14:58:24
categories: bp worklight dojo
---

#Basic Dojo Loading in Worklight apps

Proper loading of Dojo is critical for properly behaving Dojo based Worklight apps.

- First require is for primary layers
	- By default, the WL DojoLib will provide the core dojo/dojo.js and two layers:
		- core-web-layer :: Many commonly used Dojo modules
		- mobile-ui-layer :: Much of the dojox/mobile module set
	- These will e sufficient for most simple mobile apps.
- Second require is for modules explicitly needed to start the page
	- List any modules that are needed to kick-start your app.
	- The only default required entry is `dojo/domReady!`

Example:
{% highlight javascript %}
	function wlCommonInit(){
		require([
			//-- Put core layers here
		    "layers/core-web-layer",
		    "layers/mobile-ui-layer"
		], function() {
			require([
				//-- Put loose modules needed to parse the body and start the app here
			    "dojox/mobile/parser",
			    "dojox/mobile/ScrollableView",
			    "dojox/mobile/Button",
			    //-- This entry is required to ensure clean app startup, list it last.
			    "dojo/domReady!"
			], function() {
				//-- Put any startup code here
			});
		});
	}
{% endhighlight %}
