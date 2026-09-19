---
title: "Angular Generate Command"
date: "08/18/2026"
tags:
  - inbox
links:
id: "202608182026"
---

# Angular Generate Command

The generate command is used in the CLI to generate components, services, directives, and other Angular files and directories.

To use the generate command to create a new component type the folowing

```
ng generate component <name>
```

or 

```
ng g c <name>
```

This will generate a componet ts, css, and a spec file

Some options

- -d --dry-run: Run report of activities, but will not create
- -s --inline-style: Style (css file) is included in the component file
- -t --inline-template Template file is in the ts component file

Generate service

```
ng g service <name>
```

Generate directive

```
ng g directive <name>
```

List all of the files that you can generate.

```
ng g help
```
