---
title: "Anatomy of a Angular Component"
date: "08/19/2026"
tags:
  - angular
links:
id: "202608191939"
---

# Antomy of a Angular Component

The Angular Component file will content the following

- Imports: Any libraries that need to be added to the component.
- Component Decorator:
    - Selector: will be the html tag of how it is used in other templates.
    - Template: html markup of the page.
    - or TemplateUrl: is the path of the html file.
    - StyleUrl: is the path of the style file.
    - or Style: can be used in place of styleUrl where style will be added directory to the component.
- Class: Where variables and methods that are needed for that component.

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-hello',
  imports: [],
  template: `
    <p>
      new works!
    </p>
  `,
  styleUrl: './hello.css',
})
export class Hello {

}
```

