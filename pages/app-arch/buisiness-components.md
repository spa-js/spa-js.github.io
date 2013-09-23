---
layout: default
title: Business Components
category: bp, app-arch
---

# Business Components

## Introduction


![SPA layered environment](./images/app-arch-layers.png)



A Business Component is a self contained unit of work. You can think of it as a specialized black box, that can act as its own mini-application. It has no knowledge of its external environment, having a fixed set of inputs, and publishes state changes for any consumer.

A bijit is a conceptual encapsulation of a fixed set of assets. Typically, a bijit consists of a JavaScript controller and an HTML template. It may optionally support a custom Style sheet and runtime configuration.

