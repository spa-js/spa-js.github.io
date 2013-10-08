---
layout: default
title: Development - HTML
category: bp
---



# HTML Development

## Introduction

This section includes best practices regarding development of HTML source code

- Always use HTML5 declaration at the beginning of full HTML documents
	- `<!DOCTYPE html>`
	- Do not add to HTML fragments (eg template files)

- Always use the new standard UTF-8character set
	- `<meta charset="utf-8">`

- Ensure latest IE rendering engine is used by adding the following:
	- `<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">`

- Support a mobile device's viewport with:
	- `<meta name="viewport" content="width=device-width">`

- No need to include “type” attributes on `<script>` and `<style>` elements
	- Good: `<script src="libs/myJsLib.js"></script>`
	- Bad:  `<script type="text/javascript" src="libs/myJsLib.js"></script>`

- NEVER use invalid null `<script>` or `<div>` tags
	– Bad: `<script src=”./js/hello.js” />`
	– Good: `<script src=”./js/hello.js”></script>`
	– Bad: `<div id=”myTarget" />`
	– Good: `<div id=”myTarget”></div>`

- NEVER have duplicate "id" attributes
	– Potentially common in portal and mashups
	– Alternative is to use CSS classname addressing and queries
		-eg `<div class="myFirstName"></div>` and `${".myFirstNAme"}`
	- In templates, use variables to generate unique Ids
		- eg `<div id='{{ uid }}FirstName'></div>`
	- For Dojo, use "attach-points" in dijit templates, which are local to that dijit's instance.
		- eg `<div data-dojo-attach-point="dapFirstName"></div>`

- ALWAYS be consistent with tag and attribute case and quoting
	- Lowercase tag and attribute names is preferred
	- Quote all attributes, using double quotes
	- Good: `<div label="It's my life"></div>`
	- Poor: `<DIV Label='It\'s my life'></Div>`
	- See next practice for exception

- Do not use a value for boolean attributes
	- e.g. autofocus, autocomplete, required
	- Their mere presence ensures behavior is set.
	- In HTML5 this means that `required=”false”` is equivalent to `required=”true”`!
	- Good: `<input type=”email”/>`
	- Bad: `<input type=”email” required=”false”/>`

- Use semantic tag names where applicable
	- HTML5 introduces a lot of new tag names to aid in comprehension
	- Good: `<header>`, `<nav>`, etc.
	- Bad: `<div class="header">`, or `<span id="mainNav">`

- Use HTML5 features instead of JavaScript toolkit where possible
	- Example attributes include: autofocus, placeHolders, hidden, draggable, required
	- Example input types: email, url, search
	- Fall back to shims if necessary for older browsers.

- Avoid Deprecated Elements and Attributes
	- Many HTML4 elements and attributes are deprecated and should be replaced by CSS in order to separate content from presentation.
	- e.g. `<font>`, `<center>`, etc.
	- See [HTML5 Obsolete tags](http://www.w3.org/TR/html5-diff/#obsolete-elements) for a full list of deprecated tags
