## JS guidelines

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
