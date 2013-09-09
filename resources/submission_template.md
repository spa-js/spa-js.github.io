
#SPAJS - Content Submission Form
/*
This form is written in Markdown. Please follow common conventions. If you dont know MD, then just enter standard text, and we'll fix it up later.

Comments (like this one) are used to help fill out the tempalte, and can be deleted if desired.
*/


##Problem
/* Required: Describe what problem is being addressed or solved? */

Avoid global foo's


##Solution
/* Required: Fully describe the solution. Provide any installation/setup presumptions as needed. Complex solutions or setup should be written as a series of numbered steps. */

We can avoid global foo's by using the baz toolkit to create local object instances. The following shows how we use baz to solve this problem.

1. Install the [baz toolkit](http://baz.is.awesome)
2. Create a custom baz module:

	// Tab indented section indicates source code. Escape special characters
	baz.define("Foo", {
		init : function() {
		}
	});
	var foo = new Foo();


##Motivation
/* Optional: Describe why this is important */

Global foo's often conflict with bar's causing great harm to your app.


##Assumptions
/* Optional: What is believed to be true about the context of the problem? */

The baz toolkit can be used to encapsulate foo objects as instantiateable classes.


##Justification
/* Optional: Why this solution should be considered over existing principles or solutions. */

Using baz to hide foo's will save a million gigawatts of browser power.


##Alternatives
/* Optional: Describe other options that solve this or similar problems. */

The [wizbang gadget](http://wizbang.io) and [femto doodad](http://femto.org/doodads) toolkits are also capable of handling this scenario. I like using baz as it has a more direct API and is easier to use in complex projects.


##Submitter
/* Required: Provide information on yourself. Include your name, company, bio, email contact, website, github and other social contact ids.  Only provide what you want public. Anonymous submissions are not accepted. */

- Name:  Joe Coder
- Company: WickedSoft inc.
- Email: joec@wickedsoft.com
- GitHub: joe_coder
- Twitter: joeDeCoder

I've been banging out code for 80 years, with a specialty in HTML5.1, visual design, and wood carving.
