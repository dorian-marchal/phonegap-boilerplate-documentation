# Global





* * *

## Class: AppController
The object from which all the app controllers must inherit.

The controller actions are called by the router.

It is responsible for linking the different views with their layout.

Example :

```js
define(function(require) {
    'use strict';

    var AppController = require('core/AppController');

    return AppController.extend({
        name: 'my-controller',

        useLayouts: [
            require('app/views/SimpleLayout'),
        ],

        usePages: [
            require('app/views/MyPage'),
        ],

        pageForActions: {
            'my-page': { // The name property of the page
                page: 'my-page',
                layout: 'simpleLayout', // The name property of the layout
            },
        },
    });
});
```

**useLayouts**: `Array` , Required layouts
<br>
**usePages**: `Array` , Required pages
<br>
**layoutForPages**: `Object` , Link between routes, pages and layouts.
<br>


* * *










