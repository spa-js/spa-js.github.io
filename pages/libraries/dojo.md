---
layout: default
title: Libraries - Dojo
category: bp
---
# Dojo Toolkit

## Introduction

The [Dojot Toolkit](http://www.dojotoolkit.org) takes a radically different approach to being a toolkit. It makes everything available at once in its base package. There are hundreds of modules that span everything from basic APIs, widgets, mobile, animations, charting, graphing, and much more. The Dojo foundation manages all the components, so there is consistent quality, API signature, and licensing. The down side is that Dojo incurs a comparatively steep learning curve compared to JQ.

## Child Pages
- [Dojo AMD List](./dojo/Dojo_AMD_List.html)


## Dojo Coding Guidelines

- Code modules following the [Dojo style guide](http://dojotoolkit.org/community/styleGuide)
- Use `data-dojo-config` rather than `djConfig` attribute on dojo `<script>` element.

- Do not use global variables (objects) in application modules
	- With modern AMD code, hopefully globals are completely unnecessary.
	- If you do need to create/read a global, then the following pattern is preferred:

	```JS
		require([...], function(...){
			var global = this;
			...
			global.myVariable = "hello world";
		});
	```

	- For strict modules, there's a slightly more complicated syntax:

	```Javacript
		"use strict";
		require([...], function(...){
			var global = function("return this")();
			...
			global.myVariable = "hello world";
		});
	```

- Scan code for the following global variables. Do not use global reference, instead use AMD define() args
	- `dojo.`
	- `dijit.`
	- `dojox.`
	- Any other potential globals used by your application, such as `app.`

	- Note: In Dojo 1.8, you may see Dojo's "declare" function used with three or four arguments, with the first argument being a string which is the global path to the name of the class.  The string ClassName is for legacy compatibility with pre-Dojo1.7 code and in application code based on AMD can be removed. Example:

	```JavaScript
		var myClass = declare("a.b.c.ClassName",[BaseClass, Mixin1, Mixin2, ...],{
			//properties and methods map
		});
	```

	- instead use:

	```JavaScript
		var myClass = declare(BaseClass,[Mixin1, Mixin2],{
			//properties and methods map
		});
	```

- Dojo uses a custom format for [API documentation](http://dojotoolkit.org/reference-guide/1.7/util/doctools/markup.html)

### Publish and Subscribe Topic naming consistency & maintainability
- All topic names strings used in `topic.publish()` and `topic.subscribe()` should be defined in either a:
	- Common `app.js` within `topics` map, that is used by all other modules
		- Access `app.js` via AMD dependency list.
	- Dedicated "topics" module
- Scan code for `publish(` and `subscribe(` and ensure that the topic name is defined using `app.topics.MY_TOPIC` topic map names rather than hard-coded strings.


## Deprecated Dojo Modules
Do not use legacy or deprecated modules in application modules
	- Note: it is ok for these to be in Dojo Toolkit's modules

Scan code for the following deprecated modules:

- `dojo/_base/connect` : Replace with:
	-  `dojo/on` : Node event handler
	-  `dojo/aspect` : Function before, after, around calls
	-  `dojo/topic` : Loosely coupled event pub/sub notifications

- `dojo/_base/xhr` : Replace by `dojo/request`

- `dojo` : Instead of using the dojo module, use dependencies on specific smaller modules.

- `dojo/_base/kernel` : Avoid using this module which has large dependency chain. This module us not usually required directly by end developers, unless required for:
	- Creating additional modules that are part of the dojo toolkit.
	- An exception to the rule: Ok to use for `kernel.deprecated();`

- `dojo/_base/window` : Originally written to serve two main purposes:
	- Provide methods/variables to access the current document and the `<body>` element of the current document.
	- Provide functions to switch the *current document*, i.e. the document accessed by the methods/variables mentioned above, and indirectly by DOM methods where the document isn't implied by the arguments, for example `dojo.byId("xyz")`.
	- In modern code, you can usually forgo use of this module, and instead use:
		- `window`, `document`, and `document.body` global variables, or equivalent variables for the frame that you want to operate on.
		- If you need to operate on a different frame/document, all of the modern dojo DOM related methods either take a document parameter or a DOMNode parameter (which implies a document). For example:

	```JS
	require(["dojo/dom", "dojo/dom-geometry"], function(dom, domGeom){
	    var node = dom.byId("address", myDocument);
	    domGeom.setMarginBox(node, ...);
	});
	```

	- The following `dojo/_base/window` functions are DEPRECATED
		- `dojo.doc` : The old `dojo.doc` variable is accessible through `dojo/_base/window::doc`, but usually you can (and should) just access the `document` global variable to get a pointer to the document.
			-  For functions that operate on a DOMNode, you can get the document via `node.ownerDocument`.
		- `win.body()`
		- `win.global()`
		- `win.withDoc()`
		- `win.withGlobal()`

- `dojo/_base/Deferred` : Replace by `dojo/Deferred`

- `dojo/_base/sniff` : Replace by dojo/sniff

- `dojo/DeferredList` : Replace with dojo/promise/all and dojo/promise/first

- `dijit/hccss` : Replace with dojo/hccss

- `dojo/io/iframe` : Replace with dojo/request/iframe

- `dojo/io/script` : Replace with dojo/request/script

- `dojo/ready` : (1.9) Use `dojo/domReady!` AMD loader plugin instead.
	- The only caveat is that if you are using the parser and have custom javascript code to run, you should run the parser manually rather than setting `parseOnLoad:true`.

- `dojox/mobile/sniff` : (1.9) Replace with `dojo/sniff`

- `has("iphone")` : (1.9) replaced with `has("ios")` to detect iOS device.  In future, `has("iphone")` will just be for phone.

- `dijit/_BidiSupport` : (1.9) replaced with dojo config setting like `data-dojo-config="has:{'dojo-bidi': true}"`

- `dojox/charting/BidiSupport` : (1.9) replaced with dojo config setting like `data-dojo-config="has:{'dojo-bidi': true}"`

- `dojo.global` : was originally created to either:
	- access the global scope in a device independent way. (i.e for code to run on browsers and server side), see: [dojo/_base/kernel::global](http://livedocs.dojotoolkit.org/dojo/_base/kernel#global)
	- (for browser only code) access the window object such that other code could redirect the window object to point to a different frame. see: [dojo/_base/window::withGlobal](http://livedocs.dojotoolkit.org/dojo/_base/window#withglobal) and [dojo/_base/window::setContext](http://livedocs.dojotoolkit.org/dojo/_base/window#setcontext).
	- Regarding the first usage, modern AMD modules probably should not be trying to set or read global variables at all.
	- As for accessing the window object (to control scrolling, setup handlers, etc.), most application code can simply access the `window` global, rather than accessing [dojo/_base/window::global](http://livedocs.dojotoolkit.org/dojo/_base/window#withglobal).

- `lang.getObject()` : Review to make sure that global objects are not being used.
		- instead, objects should be passed as arguments or via messages.



## Dijit Templates

- Use data-dojo-type rather than dojoType
- Use data-dojo-attach-point rather than dojoAttachPoint
- Use data-dojo-attach-event rather than dojoAttachEvent
- Do not use "id" attributes.
 	- The exception is for `<label for='id'><input id='id' ...>`
	- In this case, the ID must be unique (ie. `id='FirstName${id}'` using widget's instance id)
- Use localized text strings, using standard Dojo I18N implementation.
- Utilize a single base variable to hold all instance strings
	- ie. `text : i18nTextFromNLS,` and then in template use `${text.title}`
- Use `dap*` prefix convention for data-dojo-attach-point in HTML templates
	- Ex.  `<div data-dojo-attach-point="dapGridTarget"></div>`
- Use `dea*` prefix convention for data-dojo-attach-event targets
	- This makes it obvious in the controller module when a function would be called (eg )
	- Template ex. `<button data-dojo-attach-event="onClick:daeShowButtonClicked" />`
	- Controller ex. `daeShowButtonClicked : function(evt) { ... }`
- Use AMD module ID notation (eg `foor/Bar`) notation, not dot-notation (`a.b.c`)

## Misc Tips

- Don't bind to the DOM Level 0 "onload" attribute, instead, use `dojo/domReady!` AMD loader plugin and `require()`


## Reference Links

- [IBM Dojo Toolkit - Dojo Accessibility](https://w3-connections.ibm.com/wikis/home?lang=en-us#!/wiki/W25125222b815_4ba8_aef1_a36a02f5bfd1/page/Dojo%20Accessibility)
- [Dojo 1.8 DRAFT API Docs](http://bill.dojotoolkit.org/api/)
- [Dojo API Doc cleanup - Google Docs](https://docs.google.com/document/d/17wDK-ZNL9zPuwLyBcXoBsIK0-6WQUnjRdLHR87YIYMI/edit)
- [Dojo Toolkit 2.0 DojoX Decomposition - Google Drive](https://docs.google.com/document/d/1kPufZYy7G_nK90z3TlojK7hC10BTZdTF-N2UEFpoP5M/edit)
- [Dojo2Roadmap - Preliminary](http://plan.dojotoolkit.org/projects/general-requests/wiki/Dojo2Roadmap)
- [Timeline – dojo – Trac](http://bugs.dojotoolkit.org/timeline)
- [Mobile Tests Index](http://archive.dojotoolkit.org/nightly/checkout/dojox/mobile/tests/)
- [CLA - The Dojo Foundation](http://staging.dojofoundation.org/about/claForm)
- [Technical Reference – Intel® HTML5 App Porter Tool - BETA | Intel® Developer Zone](http://software.intel.com/en-us/articles/technical-reference-intel-html5-app-porter-tool-beta?utm_source=html5weekly&utm_medium=email)
- [Chart Gallery of FusionCharts Suite XT | FusionCharts](http://www.fusioncharts.com/demos/gallery/#box-whisker-chart)
- [Server Side Dijit - James Thomas](http://jamesthom.as/blog/2013/01/15/server-side-dijit/)
- [Dojo Car Store (Globalized Version)](http://ajaxdemo.dfw.ibm.com/DojoGlobalizationDemo/DojoCarStore/)
- [Log All Dojo Events](javascript:(function()%7Bif(typeof%20dojo=='undefined')%7Bwindow.console.warn('Uhhh..%20you%20need%20to%20run%20this%20from%20a%20web%20app%20running%20the%20Dojo%20Toolkit,%20genius.%20Drag%20it%20into%20your%20browser%20toolbar%20for%20use%20later.');return;%7Delse%7Bwindow.console.log('Dojo%20logging%20enabled!');%7D;dojo.publish%20=%20function(topic,%20args)%7Bwindow.console.log('DOJO%20PUBLISHED%20EVENT:%20'%20+%20topic%20+%20'%20with%20the%20following%20arguments:');window.console.log(args);var%20f%20=%20dojo._topics%5Btopic%5D;if(f)%7Bf.apply(this,args%7C%7C%5B%5D);%7D%7D%7D)();)
- [JSure: The Javascript Checker](http://www.jsure.org/)
- [Include Dojo](javascript:void(function()%7Bvar%20s=document.createElement('script');s.src='http://o.aolcdn.com/dojo/1.3/dojo/dojo.xd.js';document.getElementsByTagName('head')%5B0%5D.appendChild(s);%7D()))
- [jQuery vs dojo vs mootools - Dom · jsPerf](http://jsperf.com/jquery-vs-dojo-vs-mootools-dom/13)
- [AppMobi](http://www.appmobi.com/index.php?q=node/154)
- [Market Insights - KnowledgeGate](https://w3-03.ibm.com/tools/knowledgegate/protect/SignIn.wss)
- [Ai Media Group: Interactive Marketing Arm for Agencies - About Us](http://aimediagroup.com/about_us.php)
- [jQuery Reel Plugin](http://jquery.vostrel.cz/reel)
- [Packages - The Dojo Foundation](http://packages.dojofoundation.org/)
- [sagittech: How to send mobile notifications using cURL and C2DM to an Android App](http://sagittech.blogspot.com/2011/10/how-to-send-mobile-notifications-using.html)
- [Log All Dojo Events](javascript:(function()%7Bif(typeof%20dojo=='undefined')%7Bwindow.console.warn('Uhhh..%20you%20need%20to%20run%20this%20from%20a%20web%20app%20running%20the%20Dojo%20Toolkit,%20genius.%20Drag%20it%20into%20your%20browser%20toolbar%20for%20use%20later.');return;%7Delse%7Bwindow.console.log('Dojo%20logging%20enabled!');%7D;dojo.publish%20=%20function(topic,%20args)%7Bwindow.console.log('DOJO%20PUBLISHED%20EVENT:%20'%20+%20topic%20+%20'%20with%20the%20following%20arguments:');window.console.log(args);var%20f%20=%20dojo._topics%5Btopic%5D;if(f)%7Bf.apply(this,args%7C%7C%5B%5D);%7D%7D%7D)();)
- [Include Dojo](javascript:void(function()%7Bvar%20s=document.createElement('script');s.src='http://o.aolcdn.com/dojo/1.3/dojo/dojo.xd.js';document.getElementsByTagName('head')%5B0%5D.appendChild(s);%7D()))
- [Wufoo · The Current State of HTML5 Forms](http://wufoo.com/html5/)
- [Dojo 1.8 Cheat Sheet by karim - Cheatography.com](http://www.cheatography.com/karim/cheat-sheets/dojo-1-8/)
- [2012 IBM Mobile Symposium - Start here! Everything you need to host the IBM Mobile Symposium](https://w3-connections.ibm.com/wikis/home?lang=en_US#/wiki/Wf71f60b3ffcf_4949_acea_d45e007c8173/page/Start%20here!%20%20Everything%20you%20need%20to%20host%20the%20IBM%20Mobile%20Symposium)
- [VirtualHostX - Mac OS X Apache Virtual Hosting](http://clickontyler.com/virtualhostx/?pref)
- [Requests](http://csantanapr.github.io/dapp-examples/dapp-request/dist/www/index.html#requestList)
- [dojo | Dojo API](http://api.dojotoolkit.org/jsdoc/dojo/1.1.1/dojo/.switch/HEAD)
- [SitePen Blog » Replacing the Flash Flickr Badge with Dojo](http://www.sitepen.com/blog/2008/06/23/replacing-the-flash-flickr-badge-with-dojo/)
- [DTK 2.0: Packages and DojoX - Google Docs](https://docs1.google.com/document/d/14JGtJSF6-LEZcL4GxbQlroggtnrcI3Z9Muq1Orm5Ydw/edit?authkey=CICxsLQI&hl=en&pli=1#)
- [Unified codebases with Dojo, Node, and RequireJS: the holy grail of DRY code | Blog | Zetafleet | Web design &amp; development | Minneapolis, MN](http://www.zetafleet.com/blog/unified-codebases-with-dojo-node-and-requirejs-the-holy-grail-of-dry)
- [rstWiki](http://tmpdocs.dojocampus.org/)

### Dojo - IBM Dojo Extensions (IDX)

- [Dashboard: IM Convergence - IBM Rational Team Concert](https://csnext.ibm.com:8002/jazz/web/projects/IBM%20One%20UI%20Dojo%20eXtensions%20IDX%20Toolkit#action=com.ibm.team.dashboard.viewDashboard)
