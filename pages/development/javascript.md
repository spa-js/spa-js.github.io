---
layout: default
title: Development - JavaScript
category: bp
---



# JavaScript Development

## Introduction

> Just because JavaScript permits sloppy programming, it is not a license to exploit such poor practice.

JavaScript is a powerful language, but care should be taken to write good clean code. Since JS is loosely typed, which enables variables to be easily coerced into different types. Its far too easy to inadvertently convert a string to a number, or worse a NaN (Not a number!).

```
	var s = "Hello World";
	var x = s - "World"; // Well this looks like it would take World from the string!
	console.log("Say Hello: ", s);   // Wha??? It displays: "Say Hello: NaN"
```

Instead of removing a substring using the above syntax is valid in some languages, and on the surface looks valid. But JavaScript thinks you want to perform a math operation, and the results are not a valid number giving us a `NaN` primitive. The whole point is to be careful, and know your language.


## General Recommendations

- NEVER use invalid null `<script/>` tag
	– Bad: `<script src=”./js/hello.js” />`
	– Good: `<script src=”./js/hello.js”></script>`
	– Good: `<script>var x = 123;</script>`

- Use explicit comparators (ie `===`) over coerced comparators (ie `==`).
	- Using coerced comparators actually says convert the value types to match and then compare them. All the following evaluate to true:
		- `"hello" == 1`
		- `"" == 0`
		- `1 == true`
	- Using the triple equals (`===`), or not equals (`!==`) forces a pure comparison

- Use shortcuts for default value assignment
	- Use `||` during assignment operations to allow for default values
		- `args = args || {}` - This ensures we can work on an expected input object
		- `var greeting = args.greeting || "Good day";`

- Put braces on the right of block definitions.
	- This is not a personal style choice. Its simply safer to do this in JavaScript.
	- Good:
	```js
		return {
			ok : true;
		};
	```
	- Bad:
	```js
		return          // returns undefined, not the expected object!
		{				// This block is valid, but no-ops!
			ok : false;
		};
	```
	- Taken from a [Talk by Doug Crawford](https://www.youtube.com/watch?feature=player_embedded&v=_EANG8ZZbRs#t=1105)

- NEVER leave dangling commas in lists and object definitions
	- It used to cause IE to throw errors.
	- All browsers allow it, but its sloppy programming
	- This error is commonly seen in define/require statements and after the last method/function of a declared class.
	- Tip when generating visual lists, use an Array and join results
		- eg. `console.log( "List of names: ", nameList.join(", ") );`
	- Bad: `var x = [0,1,2,3,];`
	– Bad: `var y = { a:1, b:”B”, c:x, };`

- Always, Always use semi-colons at the end of a line
	- Yes, JavaScript will do a best guess on end of lines
	- But, it does not always infer the programmers intention.
	- So don't guess how it will be interpreted by the compiler

- Avoid global variables
	- Always use the `var` statement to define local variables
	- Otherwise the variable is placed into the global scope, which is _almost_ always bad
	- Using AMD based loaders, eliminates globally name spaced packages/modules.
	- Does not apply browser provided globals such as: `window`, `navigator`, `document`, `console`, etc.

- Define all local `var`'s at the top of each function
	- This is not **required**, but leads to cleaner code and show intent by the programmer
	- Random `var` definitions throughout a function are sloppy and can lead to errors, such as unintented variable re-assignment.
	- Local variables are at `function` scope, meaning they are accessible anywhere within the enclosing function, not just within enclosing `{ ... }` blocks.
	- This applies to `for( var i in ...) { ... }` blocks as well.  `i` is not scoped to the for block, but its outer containing function.  This is just such a common practice in most other languages, that people expect this to be the case in JavaScript too. Its not.

- NEVER leave `debugger` statements in code
	- debugger statement can be used to force browser breakpoint
	- Better to locate desired code location and manually set breakpoint using browser tools.
	- Will break minification and optimization builds.

- Do not test variables against text strings for triggered events.
	- Condition checking should be made against variables or reference to the reference node that triggered an event, rather than against multilingual values.
	- This will reduce the chance of errors when UI values change, but the logic checking for them is mistakenly not updated.
	- It should also improve the maintainability of the code itself by actually clearly showing what the actual conditions are, just once, for a given action.
	- Example: Consider checking against the resource bundle text definition rather than one of two text translations. e.g. This is brittle coding:

	```JS
	if (acct.description.match(/^LINE OF CREDIT.*/) || acct.description.match(/^LIGNE DE CREDIT.*/)) {
	```

- Do not use hyphens in variable names.  These can get confused with subtraction attempts.
	- Example: `var hello-world = "Hi there";` results in an attempt to subtract world from hello, throwing errors.

- Follow standard variable and function naming conventions
	- Normal variables are `camelCase`
	- Private variables use leading underscore, `_myPassword`
	- Constants are all uppercase `var PI = 3.14159;`

- Do not test variables against text strings for triggered events.
	- Condition checking should be made against variables or reference to the reference node that triggered an event, rather than against multilingual values.
	- This will reduce the chance of errors when UI values change, but the logic checking for them is mistakenly not updated.
	- It should also improve the maintainability of the code itself by actually clearly showing what the actual conditions are, just once, for a given action.
	- Example: Consider checking against the resource bundle text definition rather than one of two text translations. e.g. This is brittle coding:

	```JS
		if (acct.description.match(/^LINE OF CREDIT.*/) || acct.description.match(/^LIGNE DE CREDIT.*/)) {
	```

## AMD Coding guidelines
The following section details the Asynchronous Module Definition (AMD) style of defining modules.

- Do not add modules to the callback argument list that are not directly referenced within that module's definition
	- If a module is required, but is not directly referenced within the module code, then place it at the end of the require/define dependency list, and do not give it a local variable name in the callback function's arguments.

	```JS
	define([
		"app/BaseClass",
		"dojo/_base/declare",
		"dijit/form/Button"      //-- Used by template, and not directly, so no callback ref
	], function( BasClass, declare) )
	```

- Do not repeat module identifiers in your define function.
	- Incorrect: `define(["app/widget",..,"app/widget"],function(Widget,...,Widget){...});`
	- Correct: `define(["app/widget",...],function(Widget,...){...});`

- Check dependencies list, don't include extra modules whose arg's are not used.
	- There should be an obvious 1 to 1 relationship between the dependency modules and the callback parameters
	- For large dependency lists, add a blank line every so often to break up the list
	- Likewise, in the callback list, match the breaks with a new line of arguments.
	- Having a mismatch between the dependency list and the callback arguments is the primary cause of AMD related defects

- Organize modules in the following pattern
	- Core modules (eg. Base classes, templates, NLS) unique to this module
	- Then alphabetically, grouping modules by prefix (ie dojo, dijit, dojox, myApp)
	- Modules not directly referenced in callback function should be listed last, with a descriptive group comment
		- ie. `// The following modules are used by the template, and not directly referenced in this module`

- Use standard callback argument names that match (or are very close) to the real dependency modules name
	- For Dojo modules.  See [Dojo AMD List.txt](../libraries/dojo/Dojo_AMD_List.html) for standard module to callback arg name map.




## Linting

Lint is a classic method for static code analysis. Since JavaScript is unfortunately forgiving with sloppy syntax, that can lead to hard to depict errors, Linting tools should be part of every web developer's toolbox. Many IDEs and editors do a good job of detecting syntax errors, but there is still a place for standalone Lint checkers as part of continuous integration.

Read the [JSLint documentation](http://www.jslint.com/lint.html)
- Then re-read it until you understand and accept (almost) all the rules defined.
- You **will** be a better JavaScript programmer afterwards.

Listed below are several Lint tools specifically for JavaScript

- [JSLint](http://jslint.com/) - The grandfather of JavaScript lint tools by Doug Crockford. It will also do a good job of detecting invalid HTML code. Read the instructions. Please.
- [JSHint](http://jshint.com/) - A popular fork of the original JSLint.
- [ESHint](https://github.com/nzakas/eslint) - A command line JS linter that enables a plugable list of tests. It shows promise as its more flexible than JSHint
- [JSONLint](http://jsonlint.com/)jshint.com

Recommended JSHint options
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



## Style Guides

Your company should adopt a standard style guide for coding in various languages. You typically do not need to get overly picky with styling, but having rules in place will foster a cohesive feel for your applications, and aid in general maintenance.

The most important points on styling are:
- Your code should be easy to understand
- Comment complex logic, or better yet, rewrite it to be less cryptic.

Listed below are a few good style guides. You can mix and match these recommendations to meet your group collective aesthetic requirements.

- [Dojo Style Guide]()
- [AirBnB Style Guide](https://github.com/airbnb/javascript)
- [SemanticUI Style Guide](http://semantic-ui.com/guide/javascriptguide.html)
