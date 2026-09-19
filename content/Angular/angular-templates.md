---
title: Angular Templates
date: 09/07/2026
tags:
  - angular
links:
id: "202609070918"
---
# Angular Templates

Templates are the html files of the Angular application.  The component renders the template with any functions or variables that are connected to that component.

## Interpolation

This binding is used to display a value of a method or variable.

component
```
let name = "Jack"
```

Template
```
<h2>Hello {{ name }} </h>
```

## Property binding

To bind a value to an html property

```
<button [disabled]="isLoading"/>
```

Apply a class depending on a variable value

```
<div class.enabled="!isLoading">....</div>
```

## Event binding

Event binding is to apply some sort of action to a method

Action on a click event

```
<button (click)="uploadResults()"/>
```

On a key press event

```
<input (keydown.enter)="keydown($event)"/>
```

With events you are able to pass in an variable $event which is the event itself.

## Two-way binding

Two way data binding is used to keep data in sync with another component or form control.  If an update happens in one place then it will be reflected in the other.

```
<input type="text" [(ngModel)]="name"/>
```

```
<app-counter [(count)]="count"></app-counter>
```

## Template Reference Variables

You are able to assign a DOM element or component to a variable in the template.

```
<input type="text" #myTextValue />
```

This will let you assign values or call methods on the DOM element depending on actions in the template or component
