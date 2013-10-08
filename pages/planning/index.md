---
layout: default
title: Planning
category: bp
---

# Planning

## Introduction

This document describes project planning and the decisions that need to be made that impact how an application will be created.

General application startup flow consists of:
1. User Stories
	- What is this app's purpose
	- DO NOT attempt to mirror functionality of existing desktop app
	- Define the set of goals.
		- Keep it small and focused.
		- No more than 10 "stories"
	- 10,000 foot level flow of user actions for each story
		- If its more than a few steps, its too complicated.
2. Visual Design
	- General "pencil sketch" design of app and major views
	- Base on user stories and flows
	- Prototype views based on design
		- Define general look of entire app
		- Validate functional flow and actions with users business owners
	- Finalize design (theme) and user stories
3. Deconstruction
	- Break each view into composite parts
	- These become the Business Components described in the [application architecture](../app-arch)
		- The parts may need to be further broken down into smaller contained parts
4. Development / Test
	- Development team defines work items
	- Generally divided by front-end and back-end development teams
	- Back-end team
		- Develops generic business services that meets the needs of the current app, but with a goal of general reuseability
		- Leads and works with Front-end on creation of "services contract"
		- Creates services stubs based on contract
	- Front-end
		- Application foundation defined and developed by senior developer
		- Other specialist may be used for data management, security, etc.
		- Dedicated CSS developer. Find one and pay them well.
		- Business components are developed by rest of team
	- Test cases should be defined (and preferably written) prior to code development
5. Continuous integration
	- Defined and started prior to or at the beginning of development cycle
	- Reliable build process should working during first sprint.
		- DO NOT save this for a late development sprint
	- CI should run full test suite on each build.



- [sub page 1](./subpage1.html)
- [sub page 1](./subpage1.html)
- [sub page 1](./subpage1.html)


## References
- [Some important link](http://www.ibm.com)

<!-- =====[ Keep all links inline.  It will make breaking up docs easier ]===== -->

