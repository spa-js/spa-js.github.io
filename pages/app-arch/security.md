---
layout: default
title: Security
category: bp, app-arch
---

## Introduction

- MUST review all use of eval().
	- Eval'd expression must be from trusted source to avoid security vulnerabilities.
- MUST ensure no hard coded usernames or passwords in client processed code.
- MUST ensure no passwords are persisted in localStorage/sessionStoreage/Cookies
- SHOULD ensure no usernames are persisted in localStorage/sessionStoreage/Cookies

![SPA layered environment](./images/app-arch-layers.png)


