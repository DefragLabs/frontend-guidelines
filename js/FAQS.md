## FAQ's

### Adding environment variables

This might be required to fetch the backend api url through the environment variable, making it easy for the deployment team
to deploy to multiple environments, without a code change.

They can be used for other scenarios as well, like setting log levels etc.

We can't set environment variables in the server and expect js to pick them up. JS doesn't take these during the runtime as 
the code is executed in the user's browser and not in the server. So these have to be consumed during the build time.

This document https://facebook.github.io/create-react-app/docs/adding-custom-environment-variables explains how to read values
from env variables during build time.

### React-router intercepting server routes.

Frontend javascript code intercepts the backend api calls, not allowing backend to respond to the requests. This is 
troublesome. To solve this we have to disable service worker.

We can remove this line `registerServiceWorker();` to solve this issue. 

Then one might ask, why use service workers in the first place ?

Service worker registration caches the files, this lets the app load instantly for repeated visitors.
https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Do not use index for figuring out the order

Let's take an example

```
var colors = ["red", "yellow", "blue"]
```
We might use the index of the colors to identify the order. In the above example the order is `red -> yellow -> blue`
Now let's say these come from an api. There is no guarantee that the order is maintained. It might come in a different order.

We can solve it in the following way

```
var colors = [
    {
        "name": "red",
        "index": 0
    }, {
        "name": "yellow",
        "index": 1
    }, {
        "name": "blue",
        "index": 2
    }
]
```

By using the above code, we don't infer the ordering from the index of values in an array. It doesn't matter what the order
of values in an array, we always check for the index of the color in the object.

### Use browser's local timezone while using datetime

Backend usually stores datetime in `UTC` to avoid the confusion. But when they are displayed, they have to be converted to the
timezone of the browser. Similarly, when generating any datetime values, generate them in the local timezone.
