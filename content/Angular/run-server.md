---
title: "Run Angular Development Server"
date: "08/18/2026"
tags:
  - angular
links:
id: "202608181929"
---

# Run Angular Development Server


To build the application and start a development server.  Run the following command.  The server will watch for changes in the source code and automatically reload the application when changes are detected.

```
ng serve
```

or

```
npm run start
```

By default npm run start will just run ng serve, but can be configured in the package.json file

By default the url for the application with be http://localhost:4200

To choose a different port run the following command

```
ng serve --port 4100
```

Now the server will run on 4100. 

To allow connections to the application from your IP address run

```
ng serve --host 0.0.0.0
```

0.0.0.0 is not a placeholder for your IP, it will automatically connect to your IP address.
