# Authentication

Phonegap Boilerplate support authentication via token. Authentication is opt-in.

### Server : Usage and set up

__Description :__

The server `Authentication` module creates the following routes :

- POST logout (access_token) : log the user out
- POST login (username/password) : log the user in
- GET logged-in (access_token) : check if the user is logged in (status 200 or 401)

It adds the `server.authenticateMiddleware`, an express middleware that you must use in your route to require authentication.

__Installation :__

Require the `Authentication` module :

```js
var auth = require('../core/server_modules/Authentication');
```

Add authentication to the server :

```js
auth.addTo(server); // server is a RestServer instance
```

Configure the authentication (implements 3 methods) :

```js
auth.findUserByToken = function(token, done) {
    // Code to search user by token

    // Error
    done('Error description');

    // Success (the user is returned if found)
    // /!\ Important, the returned user must have a 'token' property.
    done(null, user);
};
```

```js
auth.findUserByUsernameAndPassword = function(username, password, done) {
    // Code to search user by username/password

    // Error
    done('Error description');

    // User found
    // /!\ Important, the returned user must have a 'token' property.
    done(null, user);
};
```

```js
auth.updateUserToken = function(user, token, done) {
    // Code to update user token

    // Error
    done('Error description');

    // Success
    // If for some reason, you want to override the generated token, you can pass
    // the new token as the second parameter to the done callback.
    done();
};
```

__Authenticate a user :__

To authenticate a user, use the `authenticate` middleware :

```js
server.app.get('/my-route', server.authenticate, function (req, res) {
    // If req.user is available, the user is authentified
});
```

__Require authentication :__

If you want your route to be only accessible to authentified users, use the `requireAuthentication` middleware :

```js
server.app.get('/my-route', server.requireAuthentication, function (req, res) {
    // This method is called if the user is authentified
    // Otherwise, the user get a 401 error
});
```


### Client : Usage and set up

Add `useAuth: true` in your config file (`www/js/config.js`).

To authenticate a user, require `app/singletons/auth`, then use :

```js
auth.login(username, password, callback(loginSuccess))
```

An access token will automatically be added in each GET/POST request.

To check if a user is logged in, use the property : `auth.loggedIn`.

Later, you can access user information via `auth.user`.

Finally, to log out a user, use :

```js
auth.logout(callback)
```

### Based on

- [Passport](http://passportjs.org/)
- [Node UUID](https://github.com/broofa/node-uuid)
- [Passport HTTP Bearer](https://github.com/jaredhanson/passport-http-bearer)
