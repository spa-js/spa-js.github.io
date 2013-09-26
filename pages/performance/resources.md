---
layout: default
title: Performance - Resource Management
category: bp
---

# Performance - Resource management

The most simple of suggestions is to reduce the number of files loaded by the app.  This needs to be weighed against the need to have a manageable project structure, and overall size.  Yes, we have seen complex web apps that consist of a single humongous file! Its possible to do, but wildly unmaintainable, and incurs a big hit at startup time. Don't do that.

It is important to make it easy during development by having clean separation of concerns, and clean modular sections of the code. The build and deployment process is where you need to focus on optimizing files for performance. File optimization is discussed in detail in the [Continuous Integration document](./continuous-integration.html).  Suffice to say that from a performance perspective file optimization is the single best contributor to a better performing web app.
