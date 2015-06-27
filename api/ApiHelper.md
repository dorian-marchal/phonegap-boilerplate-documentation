# ApiHelper

$.ajax wrapper to easily make request to the server API.
An instance of ApiHelper is available as `app/singletons/api.js`

Example :
```js
var api = new ApiHelper('localhost', 8080);
api.get('/mymodels', {
    success: sucessCallback,
    error: errorCallback,
});
```



* * *

### ApiHelper.setToken(token) 

Globally add the access_token to all Ajax requests

**Parameters**

**token**: `String`, Globally add the access_token to all Ajax requests



### ApiHelper.get(route, options) 

$.ajax (GET) wrapper

**Parameters**

**route**: `String`, Your relative route.

**options**: `object`, $.ajax options



### ApiHelper.post(route, options) 

$.ajax (POST) wrapper

**Parameters**

**route**: `String`, Your relative route.

**options**: `object`, $.ajax options




* * *










