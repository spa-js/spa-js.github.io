---
layout: default
title: Globalization
category: bp, app-arch
---

# Globalization

## Introduction


- NEVER hard code strings within program code or templates
	- Always assume your app will be translated eventually.
	- At the very least, create a local map of key values for strings
	```JS
		this.text = {
			"title"  : "Greetings",
			"firestName" : "First name",
			...
		};
	```

- The browser defines the language and locale for you

- Always use double quotes for NLS'd strings.
	- Many languages make heavy use of single quotes as part of the language
	- Translators typically do not know "JSON" , and will cause invalid strings when apostrophes are introduced.
	- Example:
		- English base:  `{ 'finish' : 'The end of the story' }`
		- French translation:  `{ 'finish' : 'La fin de l'histoire' }` // <<-- ERROR!!

