# Global





* * *

## Class: AppLayout
A base layout. All the layouts of the application must inherit AppLayout.

Example :

```js
define(function (require) {
    'use strict';
    var AppLayout = require('core/views/AppLayout');

    return AppLayout.extend({
        name: 'simpleLayout',
        template: require('text!app/templates/SimpleLayout.html'),
        defaultOptions: {
            title: 'DefaultTitle',
        },
        render: function() {
            AppLayout.prototype.render.apply(this, arguments);
            return this;
        },
    });
});
```

**name**: `String` , A unique string to identify the layout in the controller.
<br>
**template**: `String` , Underscore template of the layout.
This template must have an element with the class .content that
will become the AppPage element node.
It will be compiled to `this.tpl` at init.
<br>
**subviews**: `Object` , List of AppView that will be linked to the given selector.
Example :

```js
subviews: {
    // At render, MyViewClass will be rendered in the `.selector` node
    '.selector' : MyViewClass, // Must inherit AppView
}
```
**defaultOptions**: `Object` , Default layout options that can be overriden by the pages
<br>


* * *










