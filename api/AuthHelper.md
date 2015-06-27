# Global





* * *

## Class: AuthHelper
Manage the user authentication.

**loggedIn**: `Boolean` , true if the user is logged in
<br>
### AuthHelper.AuthHelper(api) 

Manage the user authentication.

**Parameters**

**api**: `ApiHelper`, ApiHelper instance


### AuthHelper.login(username, password, callback) 

Log the user in

**Parameters**

**username**: `String`, Log the user in

**password**: `String`, Log the user in

**callback**: `function`, Called with a boolean (true = auth success)


### AuthHelper.logout(callback) 

Log the user out

**Parameters**

**callback**: `function`, Called when the user is logged out (false
is passed in parameter if an error occur)


### AuthHelper.setUser(user) 

Save the user in the localStorage

**Parameters**

**user**: `object`, User object


### AuthHelper.clearUser() 

Remove the user from the localStorage


### AuthHelper.checkLogin(callback) 

Check if the token can authenticate the user

**Parameters**

**callback**: `function`, A boolean is passed (true = loggedIn)




* * *










