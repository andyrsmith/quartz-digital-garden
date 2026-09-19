---
title: Angular Change Detection
date: 09/07/2026
tags:
  - angular
links:
id: "202609070944"
---
# Angular Change Detection

This is the process of Angular detecting changes in the component and reflecting it in the template

Angular uses Zone.js to patch the addEventLisiteners of the browser API.  This is to give us more functionallity while at the same time being optimized by performance.

## Change Detection Strategies

- onPush: check only when marked as dirty, input changes, or signals it depend on
- default: Component is always checked
