# Global





* * *

## Class: AppRouter
The object from wich the app router must inherit.
Inherit Backbone.Router.

**controllers**: `Object` , Required controllers
<br>
**routes**: `Object` , list of Backbone.Router.route bound to actions
Can contain :controller, :action and *params.

Example :

```js
customRoutes: {
    '' : 'home',
    ':action(/*params)' : 'simpleAction',
},
simpleAction: function (action, stringParams) {
    this.routeAction('ctrl', action, stringParams);
}
```
### AppRouter.routeAction(controller, action, stringParams) 

Call a controller action

**Parameters**

**controller**: `String`, Controller name

**action**: `String`, action name (default: index)

**stringParams**: `String`, List of parameters passed to the action
                             separated by '/'


### AppRouter.callAction(controller, action, params) 

Call a controller action. Call this.unknownRoute if the action is not found.

**Parameters**

**controller**: `String`, Controller name

**action**: `String`, Action name

**params**: `Array`, List of parameters


### AppRouter.unknownRoute(other) 

Called when no matching routes is found

**Parameters**

**other**: `String`, controller.action(param1, param2, ...)


### AppRouter.extractParams(stringParams) 

Convert stringParams string in array of parameters

**Parameters**

**stringParams**: `String`, List of parameters separated by '/'

**Returns**: `Array`, Parameters list



* * *










