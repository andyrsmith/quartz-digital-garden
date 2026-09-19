---
title: Angular Signals
date: 09/07/2026
tags:
  - angular
links:
id: "202609071002"
---
# Angular Signals

Signals provides a wrapper around a value to notify those parts interested when the value changes

Creating a signal

```
score = signal(0)
```

Sets up a signal value with a value passed in

To display the value

```
this.score()
```

Use the set method to change the value

```
this.score.set(10)
```

Use the update method to change the value with a function

```
this.score.update(score => score + 1)
```

Use computed to update other values when the signaled value is updated

```
derivedScore = computed(() => {
	return this.score() * 2;
})
```

