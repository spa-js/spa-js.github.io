---
layout: default
title: Single Page App Developer Checklist
category: productivity
tags: [development, lifecycle]
---

Security
--------
- MUST review all use of eval().
	- Eval'd expression must be from trusted source to avoid security vulnerabilities.
- MUST ensure no hard coded usernames or passwords in client processed code.
- MUST ensure no passwords are persisted in localStorage/sessionStoreage/Cookies
- SHOULD ensure no usernames are persisted in localStorage/sessionStoreage/Cookies

File names
----------
- SHOULD Directory names are lowercase
- SHOULD Instantiateable Class are ProperCase with leading Capital letter
- SHOULD Singleton classes are camelCase with leading letter
- SHOULD Use only standard letters in directory or file names.
	- Numbers ok, after first character
	- Do not use spaces, underscores, or hyphens

Dijit Templates
--------------
- MUST use data-dojo-type rather than dojoType
- MUST use data-dojo-attach-point rather than dojoAttachPoint
- MUST use data-dojo-attach-event rather than dojoAttachEvent
- MUST No "id" attributes.
 	- The exception is for `<label for='id'><input id='id' ...>`
	- In this case, the ID must be unique (ie. `id='FirstName${id}'` using widget's instance id)
- MUST Use localized text strings, using standard Dojo I18N implementation.
- SHOULD utilize a single base variable to hold all instance strings
	- ie. `text : i18nTextFromNLS,` and then in template use `${text.title}`
	- SHOULD Use dap* prefix for data-dojo-attach-point in HTML templates
- SHOULD Use AMD module ID notation (eg `foor/Bar`) notation, not dot-notation (`a.b.c`)


HTML main files
---------------
- MUST Use HTML5 document preamble in master documents (ie `<!DOCTYPE html>`)
- MUST Use AMD `require()` to load built layer files and scripts (including WL scripts), rather than `<script>` tags
- MUST Don't bind to the DOM Level 0 "onload" attribute, instead, use `dojo/domReady!` AMD loader plugin and `require()`
- SHOULD Use packageMap amd loader config
	- Replace by [AMD draft "map" configuration](https://github.com/amdjs/amdjs-api/wiki/Common-Config)
- SHOULD Do not use `type="text/javascript"` in `<script>` tags for HTML5 documents


JavaScript Coding guidelines
----------------------------
- SHOULD Use JSHint on modules to check for common errors. Recommended options:
	- asi : false,
	- bitwise : false,
	- boss : true,
	- browser : true,
	- couch : false,
	- curly : true,
	- debug : false,
	- devel : true,
	- dojo : true,
	- eqeqeq : true,
	- eqnull : true,
	- es5 : false,
	- evil : true,
	- expr : true,
	- forin : false,
	- globalstrict : false,
	- immed : true,
	- iterator : true,
	- jquery : false,
	- lastsemic : false,
	- laxbreak : true,
	- loopfunc : true,
	- mootools : false,
	- newcap : true,
	- noarg : true,
	- node : false,
	- noempty : false,
	- nonstandard : true,
	- nomen : false,
	- onevar : false,
	- onecase : false,
	- passfail : false,
	- plusplus : false,
	- proto : true,
	- prototypejs : false,
	- regexdash : true,
	- regexp : false,
	- rhino : false,
	- undef : false,
	- scripturl : true,
	- shadow : false,
	- strict : false,
	- sub : true,
	- supernew : true,
	- validthis : true,
	- wsh : false,
	- smarttabs : true,
	- trailing : false,
	- white : false


- SHOULD Do not test variables against text strings for triggered events.
	- Condition checking should be made against variables or reference to the reference node that triggered an event, rather than against multilingual values.
	- This will reduce the chance of errors when UI values change, but the logic checking for them is mistakenly not updated.
	- It should also improve the maintainability of the code itself by actually clearly showing what the actual conditions are, just once, for a given action.
	- Example: Consider checking against the resource bundle text definition rather than one of two text translations. e.g. This is brittle coding:

		```
	if (acct.description.match(/^LINE OF CREDIT.*/) || acct.description.match(/^LIGNE DE CREDIT.*/)) {
		```

- MUST Do not leave trailing commas in your code.  For example:
	- Incorrect: `{a : 1, b : 2,}`
	- Correct:   `{a : 1, b : 2}`
	- This error is commonly seen in define/require statements and after the last method/function of a declared class.
- MUST Do not use hyphens in variable names.  These can get confused with subtraction attempts.
	- Example: `var hello-world = "Hi there";` results in an attempt to subtract world from hello, throwing errors.
- SHOULD Follow standard variable and function naming conventions
	- Normal variables are `camelCase`
	- Private variables use leading underscore, `_myPassword`
	- Constants are all uppercase `var PI = 3.14159;`


AMD Coding guidelines
---------------------
- MUST Do not add modules to the callback argument list that are not directly referenced within that module's definition
- MUST Do not repeat module identifiers in your define function. For example:
	- Incorrect: `define(["app/widget",..,"app/widget"],function(Widget,...,Widget){...});`
	- Correct: `define(["app/widget",...],function(Widget,...){...});`
- SHOULD Check dependencies list, don't include extra modules whose arg's are not used.
- SHOULD Organize modules in the following pattern
	- Core modules (eg. Base classes, templates, NLS) unique to this module
	- Then Alphabeticlly, grouping modules by prefix (ie dojo, dijit, dojox, myApp)
	- Modules not directly referenced in callback function should be listed last, with a descriptive comment (ie `The following modules are used by the template`)
- SHOULD Use standard callback arg names for dojo modules.  See [Dojo AMD List.txt](./Dojo_AMD_List.txt) for standard module to callback arg name map.

Dojo Coding guidelines
----------------------
- SHOULD Code follows [Dojo style guide](http://dojotoolkit.org/community/styleGuide)
- SHOULD Do not use legacy or deprecated modules in application modules
	- Note: it is ok for these to be in Dojo Toolkit's modules
- MUST Use `data-dojo-config` rather than `djConfig` attribute on dojo `<script>` element.
- SHOULD Scan code for the following deprecated modules:

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

			```
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

- MUST No use of global variables (objects) in application modules
	- Note: it is ok for these to be in Dojo Toolkit's modules
	- With modern AMD code, hopefully globals are completely unnecessary.
	- If you do need to create/read a global, then the following pattern is preferred:

		```
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

- MUST Scan code for the following global variables. Dont use global reference, instead use AMD define() args
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


- API documentation (following Dojo API documentation format) for module and public functions

- SHOULD Topic naming consistency & maintainability
	- All topic names strings used in `topic.publish()` and `topic.subscribe()` should be defined in a common `app.js` under `topics` map.
	- Access `app.js` via AMD dependency list.
	- Scan code for `publish(` and `subscribe(` and ensure that the topic name is defined using `app.topics.MY_TOPIC` topic map names rather than hard-coded strings.

