# Global





* * *

## Class: AppPage
The object from which all the app pages must inherit.

**name**: `String` , the page name
Must be unique through your app.
This property is used to identify the page in the controller
Moreover, the name is added as a class on the .page
<br>
**layoutOptions**: `Object` , override the layout options
Options passed to the layout
<br>
### AppPage.onBackButton(done) 

Called when the backbutton is pressed on the current page.
pass false to the done callback to prevent history.back

**Parameters**

**done**: `function`, Must be called if you override this method.
Return false to prevent the default behavior.


### AppPage.beforeLoad(options) 

Called before the page is added to the DOM on page slide
The route parameters are passed to this function.

**Parameters**

**options**: `Object`, Load options
{
   actionArguments: [], // Array of url parameters
   history: '' // String identifying the type of loading ('first', 'forward' or 'back')
}


### AppPage.afterRender() 

Called after the page has been added to the DOM
And juste before the page transition


### AppPage.afterLoad() 

Called on page transition end (overridable)


### AppPage.beforeLeave() 

Called just before the page slide out
(just after newPage.afterRender)


### AppPage.isCurrentPage() 

The object from which all the app pages must inherit.

**Returns**: `Boolean`, true if the page is the current loadde page



* * *










