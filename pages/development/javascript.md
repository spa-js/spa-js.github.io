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

- NEVER use invalid null `<script>` tag
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
	- Tip when generating visual lists, use an Array and join results
		- eg. `console.log( "List of names: ", nameList.join(", ") );`
	- Bad: `var x = [0,1,2,3,];`
	– Bad: `var y = { a:1, b:”B”, c:x, };`

- Always, Always use semi-colons.
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


- Read the [JSLint documentation](http://www.jslint.com/lint.html)
	- Then re-read it until you understand and accept (almost) all the rules defined.
	- You **will** be a better JavaScript programmer afterwards.



## Truth and Truthyness

JavaScript's coercion can blur the lines when it comes to the truth. This does not mean lies, but rather it tries to help turn greys into black and white.  Typically this is what we want, but it does come with potential pitfalls.

- Don't over analyze "truthy" values
	- Using coercion for truthy tests is often desirable -- if it adds clarity.
	- If you want to check if a variable is set/unset, its easy and obvious to simply test it like this
		- `if ( !myVal ) { /*Value is not set*/ }`
	- Often times, you'll see this more convoluted code that is actually more fragile and hard to grok
		- `if ( myVal === null || typeof myVal === 'undefined')  { /*Value is not set*/ }`

- Don't rely on coercion for boolean values
	- When making boolean assignments, force true or false, not truthy/falesy.
		- Bad: `var hasErrors = errors.length;` - hasErrors is now 0 (falesy), or a number (truthy).
	- Will cause the following to fail
		- `if ( hasErrors === true ) { /* we'd never get here! */ }`
	- Force a proper boolean like so:
		- Good: `var hasErrors = (errors.length > 0)` - hasErrors is now a real boolean.
		- Good: `var hasErrors = !!errors.length;` -  - hasErrors is now a real boolean.
			- The first bang negates the number to a boolean, the second negates it back to its expected value. Once you accept this, its obvious and very clean.
	- Now the above `if` test will pass properly.
	- But again, under this explicit condition, a truthy test would have been best, and avoided confusion and potential bugs.
		- `if ( hasErrors ) { // we'll get here in all expected conditions! }`
	- Avoid this situation, by being explicit on assignments, and implicit on tests.


## Common Errors

## Know your scope

JavaScript functions have a concept of "scope". This is a powerful concept, but can be confusing to novice (and senior) developers. Scope controls the `this` variable, and represents what the function effects by default. For example, if you have a Button object and you assign an onclick handler, the callback function will by default run under the scope of the Button instance. This allows you to effect the button using statements like `this.disabled = true;`. Often times, the default scope is what you want, but other times, especially in closures and callbacks, you may need to force a different scope.  There are several ways to do this.



## Style Guides

Your company should adopt a standard style guide for coding in various languages. You typically do not need to get overly picky with styling, but having rules in place will foster a cohesive feel for your applications, and aid in general maintenance.

The most important points on styling are:
- Your code should be easy to understand
- Comment complex logic, or better yet, rewrite it to be less cryptic.

Listed below are a few good style guides. You can mix and match these recommendations to meet your group collective aesthetic requirements.

- [Dojo Style Guide]()
- [AirBnB Style Guide](https://github.com/airbnb/javascript)
- [SemanticUI Style Guide](http://semantic-ui.com/guide/javascriptguide.html)