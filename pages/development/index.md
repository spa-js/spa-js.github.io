---
layout: default
title: Development and Debugging
category: bp
---

# Development and Debugging

## Introduction

This document details the best practices associated with development and debugging applications.

- [HTML](./html.html)
- [JavaScript](./javascript.html)
- [CSS](./css.html)
- [Images](./images.html)
- [Responseive Design](./responsive-design.html)
- [Testing](./testing.html)
- [Accessibilityy](./accessibility.html)
- [Globalization](./globalization.html)


## Clean Coding
Writing clean and maintainable code should be a priority for every developer. Sloppy programming practices is unprofessional, and shows disdain for your fellow programmers.

- Coding Style guides
	- Spacing and indentation
- logging
- comments
- Directory and file names

- ALWAYS write to the latest standards (HTML5, CSS3, EMCA Script 5).
	- This will keep you safe
	- Use shim toolkits to bolster older browsers.

See the [Web Coding Checklist](./web_coding_checklist.html) for general guidance on code reviews.


## Code Editing

Using a proper editor will greatly improve your efficiency as a developer. It really doesn't matter if you use a fully integrated development environment (IDE), or a simple text editor and command line tools for building and deploying. The trend seems to be moving in favor of normal text editors and open source command line tools as a development environment, as this can allow developers to focus on the task of actual coding without the distractions, slow editing, and learning curve inherent in most IDE's.

Using command line tooling for build, test and deployment, goes right in hand with continuous integration. If the developers are using the exact same process flow as the CI automation, then issues can be identified much earlier.


## Source Code Control

This is a must in terms of project management, backup and, and team development.  There are many options, but ensure that you use an SCCS for all development.  The only recommended practice is, don't deliver any changes unless it has been properly unit tested. There is nothing worse than pulling in new changes form another developer that breaks the build or kills the app. Some shops go so far as public humiliation of sloppy and uncaring developers that cause other this sort of pain. A "hat of shame" that must be worn by the scorned can work wonders to dissuade this sort of behavior.

## Project Structure

Some projects types, such as IBM Worklight, have a fixed project structure. Within that structure there may be company or personal conventions to define where assets are located. Contained below are generally accepts de-facto conventions that should be followed.

### Directory and File names
- Directory names should be lowercase
- Module naming
	- Instantiateable Class are ProperCase with leading Capital letter
	- Singleton classes are camelCase with leading letter
	- All other files should generally be camelCase, with well defined extensions.
- Use only standard letters in directory and file names.
	- Numbers are ok, after first character, but should generally be avoided unless there is a valid reason.
	- Do not embed version numbers in source file names. There is never a valid reason to do this.
	- Do not use spaces, underscores, or hyphens

### Other considerations
- Custom application code and modules should be located in an `/app` directory
- CSS and image files should be located into a common `/theme` or `/css` directory
	- This makes management and optimzation of image artifacts much easier than having them spread around the app.
	- The possible exception is for images that are tightly associated with given widget, or content.
- 3rd party libraries should be located into a `lib` or `resources` directory
	- Also, note that these should NOT be checked into source control. Use a package manager to ensure that all developers and CI flows are using consistent versions of libraries.
- Always use relative based path names for everything.
	- Always be aware of developer/CI operating system differences.
	- Do not define fixed fully qualified directory names in any code or configurations. `C:\dev\libs` does not do a Linux or OSX based developer any good.


<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->


