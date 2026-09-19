---
title: "Conditions in Angular Templates"
date: "08/20/2026"
tags:
  - angular
links:
id: "202608201924"
---

# Conditions in Angular Templates

If/else statement in Angular template are used in the following ways.

## If

To display based on condition use an @if () {} syntax

```
@if (showHeader) {
	<h1>Hello Everybody!</h1>
}
```

If showHeader is equal to true then the content will display.  

We could also use a method too

```
@if (showHeader()) {
	....
}
```


## else if and else

Else if and else are done in a similar to the if, except of course else doesn't have a condition and just to catch what didn't fall in the if and/or else if.

```
@if (showHeader) {
	....
} 
@else if (showSecondHeader) {
	...
} 
@else {
	...
}
```

