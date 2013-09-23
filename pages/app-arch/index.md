---
layout: default
title: Application Architecture
category: bp, app-arch
---

# Application Architecture

## Introduction

This document details the best practices when designing modern desktop and mobile single page apps (SPAs). It is critical to have a well thought out architecture at the client tier. Far too often, large enterprise applications employ architects to design and define he overall topology, and server-side interactions. Then when it comes to the client -- where in modern apps where the majority of business logic, 100% of the user interaction and a large part of the data processing occurs -- it is entirely represented by a simple browser icon.  The client tier must be analyzed and broken down into its logical components. There are several different layers of functionality that impact SPAs, as shown in the following figure.

![SPA layered environment](./images/app-arch-layers.png)

In this section we will break down the various areas of the client tier and describe the importance of each area, and how to utilize each to ensure a high quality and performant solution.


## [O/S and Cordova Bridge](./os-cordova.html)

## [Browser Runtime](./browser.html)

## [Shims and Polyfills](./shims.html)

## [Toolkits](./toolkits.html)

## [Application Foundation](./app-foundation.html)

## [Views](./views.html)

## [Business Components](./business-components)

## [Data Management](./data-management)

## [Services](./services.html)

## [Security](./security)

