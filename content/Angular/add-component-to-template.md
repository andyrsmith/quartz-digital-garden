---
title: "Add Component to Template"
date: "08/19/2026"
tags:
  - angular
links:
id: "202608191933"
---

# Add Component to Template

To add a component to a template first in the parent component import the child component.


```
import { Hello } from './hello/hello'

@Component({
	imports: [Hello]
})
```

Then in the parent template add the html selector of that component where you wish to display the content.

```
<app-hello></app-hello>
```



