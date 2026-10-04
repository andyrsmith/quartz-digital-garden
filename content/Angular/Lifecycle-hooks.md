---
title: Lifecycle Hooks
date: 10/04/2026
tags:
  - angular
links:
id: "202610040915"
---
# Lifecycle Hooks

Angular lifecycle hooks are a series of steps that happen from the creation to the deletion of a component.

A few of the most popular lifecycle methods.

- ngOnInit: Runs only at the beginning of the component creation when all inputs have been initialized.

- ngOnChanges: Runs every time an input changed value.  Contains a variable of type simpleChanges which contains the inputs with the old and new value of each.

- ngOnDestroy: Runs right before the component is destroyed.  Good practice to unsubscribe to any observable here.   