---
title: "Angular Services"
date: "09/21/2026"
tags:
  - angular
---


# Angular Services Dependency Injections

Services perform functions like retreiving data and other functionality that can be shared amoung many different components.

To share the service with multiple component first set @Injectable({ providedIn: 'root' }) on top of file.  This makes the service a singleton object in which the same instances is used throughout the app.  

```
@Injectable({
  providedIn: 'root',
})
export class RetreiveStreaming {
  jsonDataUrl = '/assets/streaming.json';

  constructor(private http: HttpClient) {}

  getStreamingServices(): Observable<Streaming[]> {
    return this.http.get<Streaming[]>(this.jsonDataUrl);
  }
}
```


To inject the services import the inject module from Angular and then use that to inject it into the component

```
import { inject } from "@angular/core"
import { RetreiveStreaming } from '../core/services/retreive-streaming';

private retreiveStreaming = inject(RetreiveStreaming)
```

or add it to the constructor params and you will not need the inject module

```
import { RetreiveStreaming } from '../core/services/retreive-streaming';

export class StreamingListing implements OnInit {
	constructor(private StreamingService: streamingService) {}
}
```
